# Extensions research

`Timing`: 29/03/2019

## Selected use cases for MVP

### Out of alpha

#### List current errors and identify missing ones

Errors are represented as map containing well defined keys. It closely relates to the `trace` structure.
Result of `parse` returns a map containing eventually a vector of `errors`. It is up to the consumer to decide what to do depending on those errors.

##### Error structure

An error is a map composed of the following keys: `category`, `type`, `context` and `target`.

Errors fall down into 2 main `categories`:

* `format`: failure to read the extension (incorrect EDN)
* `syntax`: failure to parse the extension

Parse errors are related to the semantic applied to the EDN format.

* incorrect keys (missing, unknown)
* incorrect values (incorrect syntax, depends on value type)

`context` is a map whose structure depends on the error type and target (.e.g {:message "Invalid .."})

`type` characterizes the error: `ìnvalid`, `missing`, `unknown` or `overriden`.

`target` is a map composed of the following keys:

* `key` the element key (e.g. 'meta or 'views/my-view)
* `type` the type (e.g. view/query/event, block, reference, type, format, property, bindings)

##### Examples

```clojure
{:category :format :type :reader}
{:category :format :type :invalid :target {:type :key :key 'meta} :context {:data {..}}}
{:category :format :type :unknown :target {:type :key :key 'unknown}}
{:category :format :type :missing :target {:type :key :key 'meta}}
{:category :format :type :overriden :target {:type :key :key 'views/view}}

{:category :syntax :type :invalid :target {:type :reference :key 'views/sds :location [0]} :context {:data [unknown {}]}}
{:category :syntax :type :invalid :target {:type :bindings :key 'views/sds :location [0]} :context {:type :assoc :data []}}
{:category :syntax :type :invalid :target {:type :block :key 'views/sds :location [0]} :context {:type 'let :data [] :reason :body}}
{:category :syntax :type :invalid :target {:type :block :key 'views/sds :location [0 1]} :context {:type 'if :data [] :reason :too-many-clauses}}
{:category :syntax :type :invalid :target {:type :view :key 'views/sds} :context {:location [0 1 0]}}
{:category :syntax :type :unknown :target {:type :reference :key 'view/sds} :context {:location [1]}}
```

#### Conduct risk assessment of all existing, potential or requested primitives

All primitives can potentially leak private information. To surface this information to the end user ech primitive will define a `permission` set that details the potential associated risk.

Some priitives can make private data available (e.g. an input file might make some local file available; a location event might leak the user location). Some other primitives can let this information escape status (e.g. an http event; an image with a specially crafted URL).
Privacy risks emerges from the combination of both.