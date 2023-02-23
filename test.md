# Objects
* [`Calendly Cloud Resources Schema`](#reference-calendly-cloud-resources-schema) (root object)




---------------------------------------
<a name="reference-calendly-cloud-resources-schema"></a>
## Calendly Cloud Resources Schema

**`Calendly Cloud Resources Schema` Properties**

|   |Type|Description|Required|
|---|---|---|---|
|**serviceName**|`string`|| &#10003; Yes|
|**envDefaults**|`object`||No, default: `{}`|
|**buckets**|[`bucket`](#reference-bucket) `[]`||No, default: `{}`|
|**postgresql**|[`postgresql`](#reference-postgresql) `[]`||No, default: `[]`|
|**topics**|[`topic`](#reference-topic) `[]`||No, default: `{}`|
|**subscriptions**|[`subscription`](#reference-subscription) `[]`||No, default: `{}`|
|**redis**|[`redis`](#reference-redis) `[]`||No, default: `{}`|

Additional properties are allowed.

### Calendly Cloud Resources Schema.serviceName

* **Type**: `string`
* **Required**:  &#10003; Yes

### Calendly Cloud Resources Schema.envDefaults

* **Type**: `object`
* **Required**: No, default: `{}`

### Calendly Cloud Resources Schema.buckets

* **Type**: [`bucket`](#reference-bucket) `[]`
* **Required**: No, default: `{}`
* **Examples**:
    * `{"name": "infra-config-bucket", "cors": [  {   "origin": [    "http://example.appspot.com"   ],   "responseHeader": [    "Content-Type"   ],   "method": [    "GET",    "HEAD",    "DELETE"   ],   "maxAgeSeconds": 3600  } ], "kmsKey": "projects/my-pet-project/locations/us-east1/keyRings/my-key-ring/cryptoKeys/my-key", "lifecycleRule": [  {   "action": {    "type": "Delete"   },   "condition": {    "age": 7   }  } ], "location": "us", "logBucket": "my-log-bucket", "gcp": {  "storageClass": "coldline" }, "versioning": true}`

### Calendly Cloud Resources Schema.postgresql

* **Type**: [`postgresql`](#reference-postgresql) `[]`
* **Required**: No, default: `[]`
* **Examples**:
    * `{"pg_version": 14, "plan": "startup-4", "tags": {}}`

### Calendly Cloud Resources Schema.topics

* **Type**: [`topic`](#reference-topic) `[]`
* **Required**: No, default: `{}`
* **Examples**:
    * `{"infra-topic": {  "name": "infra-topic" }}`

### Calendly Cloud Resources Schema.subscriptions

* **Type**: [`subscription`](#reference-subscription) `[]`
* **Required**: No, default: `{}`
* **Examples**:
    * `{"mySubscription": {  "topicName": "mytopic",  "deadletter": {   "enabled": true  } }}`

### Calendly Cloud Resources Schema.redis

* **Type**: [`redis`](#reference-redis) `[]`
* **Required**: No, default: `{}`


## Examples

* `{"gcp": {  "serviceAccount": {   "create": true,   "annotations": {}  },  "projectId": "staging-1234",  "projectNumber": 700604769710 }, "bucketDefaults": {  "versioning": true }, "buckets": {  "component-bucket": {   "name": "infra-config-bucket",   "versioning": true  } }, "postgresDefaults": {  "aivenProject": "calendly-staging",  "cloudName": "google-us-east4",  "maintenanceWindowDow": "friday",  "maintenanceWindowTime": 82800,  "pg_version": 14,  "plan": "startup-4",  "projectVpcId": "asdfasdf",  "terminationProtection": true }, "postgresql": {  "pg_version": 14,  "plan": "startup-4",  "tags": {} }, "topics": {  "infra-topic": {   "name": "infra-topic"  } }, "subscriptions": {  "mySubscription": {   "topicName": "mytopic",   "deadletter": {    "enabled": true   }  } }}`






---------------------------------------
<a name="reference-postgresql"></a>
## PostgreSQL Database

**`PostgreSQL Database` Properties**

|   |Type|Description|Required|
|---|---|---|---|
|**pgVersion**|`integer`|| &#10003; Yes|
|**dbName**|`string`|| &#10003; Yes|
|**diskSpace**|`string`||No, default: |
|**plan**|`string`||No, default: `"startup-4"`|
|**tags**|`object`||No, default: `{}`|

Additional properties are allowed.

### postgresql.pgVersion

* **Type**: `integer`
* **Required**:  &#10003; Yes

### postgresql.dbName

* **Type**: `string`
* **Required**:  &#10003; Yes
* **Pattern**: `^[a-z0-9]([-a-z0-9]*[a-z0-9])?(\.[a-z0-9]([-a-z0-9]*[a-z0-9])?)*`

### postgresql.diskSpace

* **Type**: `string`
* **Required**: No, default: 
* **Pattern**: `^[1-9][0-9]*(GiB|G)*`

### postgresql.plan

* **Type**: `string`
* **Required**: No, default: `"startup-4"`
* **Allowed values**:

### postgresql.tags

* **Type**: `object`
* **Required**: No, default: `{}`
* **Type of each property**: `string`
* **Examples**:
    * `{"team": "teamA"}`




---------------------------------------
<a name="reference-redis"></a>
## Redis Schema

**`Redis Schema` Properties**

|   |Type|Description|Required|
|---|---|---|---|
|**name**|`string`|| &#10003; Yes|
|**region**|`string`||No|
|**highlyAvailable**|`boolean`||No|
|**replicaCount**|`integer`||No|
|**version**|`string`||No|
|**memoryGb**|`integer`|| &#10003; Yes|
|**maintenanceWindowDow**|`string`||No|
|**maintenanceWindowHour**|`integer`||No|

Additional properties are allowed.

### redis.name

* **Type**: `string`
* **Required**:  &#10003; Yes

### redis.region

* **Type**: `string`
* **Required**: No

### redis.highlyAvailable

* **Type**: `boolean`
* **Required**: No

### redis.replicaCount

* **Type**: `integer`
* **Required**: No

### redis.version

* **Type**: `string`
* **Required**: No

### redis.memoryGb

* **Type**: `integer`
* **Required**:  &#10003; Yes

### redis.maintenanceWindowDow

* **Type**: `string`
* **Required**: No

### redis.maintenanceWindowHour

* **Type**: `integer`
* **Required**: No




---------------------------------------
<a name="reference-subscription"></a>
## Subscription Schema

**`Subscription Schema` Properties**

|   |Type|Description|Required|
|---|---|---|---|
|**ackDeadlineSeconds**|`integer`||No, default: `10`|
|**deadletter**|`object`||No, default: `{}`|
|**enableExactlyOnceDelivery**|`boolean`||No, default: `false`|
|**enableMessageOrdering**|`boolean`||No, default: `false`|
|**expirationTTL**|`string`||No|
|**filter**|`string`||No|
|**messageRetentionDuration**|`string`||No|
|**pushConfig**|`object`||No, default: `{}`|
|**retainAckedMessages**|`boolean`||No, default: `false`|
|**retryPolicy**|`object`||No, default: `{}`|
|**topicName**|`string`|| &#10003; Yes|

Additional properties are allowed.

### subscription.ackDeadlineSeconds

* **Type**: `integer`
* **Required**: No, default: `10`

### subscription.deadletter

* **Type**: `object`
* **Required**: No, default: `{}`

### subscription.enableExactlyOnceDelivery

* **Type**: `boolean`
* **Required**: No, default: `false`

### subscription.enableMessageOrdering

* **Type**: `boolean`
* **Required**: No, default: `false`

### subscription.expirationTTL

* **Type**: `string`
* **Required**: No
* **Pattern**: `^[0-9]*[\.]?[0-9]*s`

### subscription.filter

* **Type**: `string`
* **Required**: No

### subscription.messageRetentionDuration

* **Type**: `string`
* **Required**: No
* **Pattern**: `^[0-9]*[\.]?[0-9]*s`

### subscription.pushConfig

* **Type**: `object`
* **Required**: No, default: `{}`

### subscription.retainAckedMessages

* **Type**: `boolean`
* **Required**: No, default: `false`

### subscription.retryPolicy

* **Type**: `object`
* **Required**: No, default: `{}`

### subscription.topicName

* **Type**: `string`
* **Required**:  &#10003; Yes


## Examples

* `{"topicName": "mytopic", "deadletter": {  "enabled": true }}`


---------------------------------------
<a name="reference-bucket"></a>
## The GCS Bucket Schema

**`The GCS Bucket Schema` Properties**

|   |Type|Description|Required|
|---|---|---|---|
|**name**|`string`|| &#10003; Yes|
|**cors**|`object` `[]`|| &#10003; Yes|
|**kmsKey**|`string`||No, default: |
|**location**|`string`||No, default: `"us"`|
|**logBucket**|`string`||No, default: |
|**lifecycleRule**|`object` `[]`||No, default: `[]`|
|**versioning**|`boolean`||No, default: `false`|
|**gcp**|`object`||No, default: `{}`|

Additional properties are allowed.

### bucket.name

* **Type**: `string`
* **Required**:  &#10003; Yes

### bucket.cors

* **Type**: `object` `[]`
* **Required**:  &#10003; Yes
* **Examples**:
    * `{"cors": [  {   "origin": [    "http://example.appspot.com"   ],   "responseHeader": [    "Content-Type"   ],   "method": [    "GET",    "HEAD",    "DELETE"   ],   "maxAgeSeconds": 3600  } ]}`

### bucket.kmsKey

* **Type**: `string`
* **Required**: No, default: 
* **Pattern**: `^projects/[0-9a-z\-]+/locations/.*`
* **Examples**:
    * `"[object Object]"`

### bucket.location

* **Type**: `string`
* **Required**: No, default: `"us"`

### bucket.logBucket

* **Type**: `string`
* **Required**: No, default: 
* **Examples**:
    * `"[object Object]"`

### bucket.lifecycleRule

* **Type**: `object` `[]`
* **Required**: No, default: `[]`

### bucket.versioning

* **Type**: `boolean`
* **Required**: No, default: `false`

### bucket.gcp

* **Type**: `object`
* **Required**: No, default: `{}`
* **Examples**:
    * `{"gcp": {  "storageClass": "coldline" }}`






---------------------------------------
<a name="reference-topic"></a>
## Topic Schema

**`Topic Schema` Properties**

|   |Type|Description|Required|
|---|---|---|---|
|**name**|`string`|| &#10003; Yes|
|**kmsKey**|`string`||No, default: |

Additional properties are allowed.

### topic.name

* **Type**: `string`
* **Required**:  &#10003; Yes
* **Examples**:
    * `"infra-topic"`

### topic.kmsKey

* **Type**: `string`
* **Required**: No, default: 
* **Pattern**: `^projects/[0-9a-z\-]+/locations/.*`
* **Examples**:
    * `"[object Object]"`


## Examples

* `{"name": "infra-topic"}`
