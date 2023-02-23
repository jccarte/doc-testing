

---------------------------------------
<a name="reference-calendly-cloud-resources-schema"></a>
## Calendly Cloud Resources Schema

**`Calendly Cloud Resources Schema` Properties**

|   |Type|Description|Required|
|---|---|---|---|
|**serviceName**|`string`|Name of the Calendly service| &#10003; Yes|
|**envDefaults**|`object`|Environment Defaults Schema|No, default: `{}`|
|**buckets**|[`bucket`](#reference-bucket) `[]`|GCS Bucket Schema|No, default: `{}`|
|**postgresql**|[`postgresql`](#reference-postgresql) `[]`|Aiven PostgresQL Schema|No, default: `[]`|
|**topics**|[`topic`](#reference-topic) `[]`|GCP PubSub Topics|No, default: `{}`|
|**subscriptions**|[`subscription`](#reference-subscription) `[]`|The subscriptions Schema|No, default: `{}`|
|**redis**|[`redis`](#reference-redis) `[]`|Redis Schema|No, default: `{}`|

Additional properties are allowed.

### Calendly Cloud Resources Schema.serviceName

Name of the Calendly service

* **Type**: `string`
* **Required**:  &#10003; Yes

### Calendly Cloud Resources Schema.envDefaults

Environment Defaults Schema

* **Type**: `object`
* **Required**: No, default: `{}`

### Calendly Cloud Resources Schema.buckets

GCS Bucket Schema

* **Type**: [`bucket`](#reference-bucket) `[]`
* **Required**: No, default: `{}`

### Calendly Cloud Resources Schema.postgresql

Aiven PostgresQL Schema

* **Type**: [`postgresql`](#reference-postgresql) `[]`
* **Required**: No, default: `[]`

### Calendly Cloud Resources Schema.topics

GCP PubSub Topics

* **Type**: [`topic`](#reference-topic) `[]`
* **Required**: No, default: `{}`

### Calendly Cloud Resources Schema.subscriptions

The subscriptions Schema

* **Type**: [`subscription`](#reference-subscription) `[]`
* **Required**: No, default: `{}`

### Calendly Cloud Resources Schema.redis

Redis Schema

* **Type**: [`redis`](#reference-redis) `[]`
* **Required**: No, default: `{}`




---------------------------------------
<a name="reference-postgresql"></a>
## PostgreSQL Database

**`PostgreSQL Database` Properties**

|   |Type|Description|Required|
|---|---|---|---|
|**pgVersion**|`integer`|PostgreSQL Version| &#10003; Yes|
|**dbName**|`string`|Database Name| &#10003; Yes|
|**diskSpace**|`string`|The disk space of the service, possible values depend on the service type, the cloud provider and the project. Reducing will result in the service re-balancing|No, default: |
|**plan**|`string`|Aiven PostgreSQL Service Plan|No, default: `"startup-4"`|
|**tags**|`object`|key:value tags|No, default: `{}`|

Additional properties are allowed.

### postgresql.pgVersion

PostgreSQL Version

* **Type**: `integer`
* **Required**:  &#10003; Yes

### postgresql.dbName

Database Name

* **Type**: `string`
* **Required**:  &#10003; Yes
* **Pattern**: `^[a-z0-9]([-a-z0-9]*[a-z0-9])?(\.[a-z0-9]([-a-z0-9]*[a-z0-9])?)*`

### postgresql.diskSpace

The disk space of the service, possible values depend on the service type, the cloud provider and the project. Reducing will result in the service re-balancing

* **Type**: `string`
* **Required**: No, default: 
* **Pattern**: `^[1-9][0-9]*(GiB|G)*`

### postgresql.plan

Aiven PostgreSQL Service Plan

* **Type**: `string`
* **Required**: No, default: `"startup-4"`
* **Allowed values**:

### postgresql.tags

key:value tags

* **Type**: `object`
* **Required**: No, default: `{}`
* **Type of each property**: `string`




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
|**ackDeadlineSeconds**|`integer`|This value is the maximum time after a subscriber receives a message before the subscriber should acknowledge the message.|No, default: `10`|
|**deadletter**|`object`|Whether to set up a deadletter topic with `deadletter.enabled`|No, default: `{}`|
|**enableExactlyOnceDelivery**|`boolean`|If 'true', Pub/Sub provides the following guarantees for the delivery of a message with a given value of messageId on this Subscriptions': - The message sent to a subscriber is guaranteed not to be resent before the message's acknowledgement deadline expires. - An acknowledged message will not be resent to a subscriber. Note that subscribers may still receive multiple copies of a message when 'enable_exactly_once_delivery' is true if the message was published multiple times by a publisher client. These copies are considered distinct by Pub/Sub and have distinct messageId values.|No, default: `false`|
|**enableMessageOrdering**|`boolean`|Immutable. If 'true', messages published with the same orderingKey in PubsubMessage will be delivered to the subscribers in the order in which they are received by the Pub/Sub system. Otherwise, they may be delivered in any order.|No, default: `false`|
|**expirationTTL**|`string`|Specifies the 'time-to-live' duration for an associated resource. The resource expires if it is not active for a period of ttl. If ttl is not set, the associated resource never expires. A duration in seconds with up to nine fractional digits, terminated by 's'. Example - '3.5s'.|No, default: |
|**filter**|`string`|Immutable. The subscription only delivers the messages that match the filter.|No, default: |
|**messageRetentionDuration**|`string`|How long to retain unacknowledged messages in the subscription's backlog, from the moment a message is published.|No, default: `"604800s"`|
|**pushConfig**|`object`|If push delivery is used with this subscription, set `pushConfig.endpoint`|No, default: `{}`|
|**retainAckedMessages**|`boolean`|Indicates whether to retain acknowledged messages.|No, default: `false`|
|**retryPolicy**|`object`||No, default: `{}`|
|**topicName**|`string`|The topic to subscribe to.| &#10003; Yes|

Additional properties are allowed.

### subscription.ackDeadlineSeconds

This value is the maximum time after a subscriber receives a message before the subscriber should acknowledge the message.

* **Type**: `integer`
* **Required**: No, default: `10`

### subscription.deadletter

Whether to set up a deadletter topic with `deadletter.enabled`

* **Type**: `object`
* **Required**: No, default: `{}`

### subscription.enableExactlyOnceDelivery

If 'true', Pub/Sub provides the following guarantees for the delivery of a message with a given value of messageId on this Subscriptions': - The message sent to a subscriber is guaranteed not to be resent before the message's acknowledgement deadline expires. - An acknowledged message will not be resent to a subscriber. Note that subscribers may still receive multiple copies of a message when 'enable_exactly_once_delivery' is true if the message was published multiple times by a publisher client. These copies are considered distinct by Pub/Sub and have distinct messageId values.

* **Type**: `boolean`
* **Required**: No, default: `false`

### subscription.enableMessageOrdering

Immutable. If 'true', messages published with the same orderingKey in PubsubMessage will be delivered to the subscribers in the order in which they are received by the Pub/Sub system. Otherwise, they may be delivered in any order.

* **Type**: `boolean`
* **Required**: No, default: `false`

### subscription.expirationTTL

Specifies the 'time-to-live' duration for an associated resource. The resource expires if it is not active for a period of ttl. If ttl is not set, the associated resource never expires. A duration in seconds with up to nine fractional digits, terminated by 's'. Example - '3.5s'.

* **Type**: `string`
* **Required**: No, default: 
* **Pattern**: `^[0-9]*[\.]?[0-9]*s`

### subscription.filter

Immutable. The subscription only delivers the messages that match the filter.

* **Type**: `string`
* **Required**: No, default: 

### subscription.messageRetentionDuration

How long to retain unacknowledged messages in the subscription's backlog, from the moment a message is published.

* **Type**: `string`
* **Required**: No, default: `"604800s"`
* **Pattern**: `^[0-9]*[\.]?[0-9]*s`

### subscription.pushConfig

If push delivery is used with this subscription, set `pushConfig.endpoint`

* **Type**: `object`
* **Required**: No, default: `{}`

### subscription.retainAckedMessages

Indicates whether to retain acknowledged messages.

* **Type**: `boolean`
* **Required**: No, default: `false`

### subscription.retryPolicy

* **Type**: `object`
* **Required**: No, default: `{}`

### subscription.topicName

The topic to subscribe to.

* **Type**: `string`
* **Required**:  &#10003; Yes




---------------------------------------
<a name="reference-bucket"></a>
## The GCS Bucket Schema

**`The GCS Bucket Schema` Properties**

|   |Type|Description|Required|
|---|---|---|---|
|**name**|`string`|Bucket Base Name| &#10003; Yes|
|**cors**|`object` `[]`|Bucket CORS Rules| &#10003; Yes|
|**kmsKey**|`string`|KMS Key self link to use.|No, default: |
|**location**|`string`|The GCS Bucket Location|No, default: `"us"`|
|**logBucket**|`string`|GCS Logging Bucket|No, default: |
|**lifecycleRule**|`object` `[]`|GCS lifecycleRules|No, default: `[]`|
|**versioning**|`boolean`|Bucket Versioning Boolean|No, default: `false`|
|**gcp**|`object`||No, default: `{}`|

Additional properties are allowed.

### bucket.name

Bucket Base Name

* **Type**: `string`
* **Required**:  &#10003; Yes

### bucket.cors

Bucket CORS Rules

* **Type**: `object` `[]`
* **Required**:  &#10003; Yes

### bucket.kmsKey

KMS Key self link to use.

* **Type**: `string`
* **Required**: No, default: 
* **Pattern**: `^projects/[0-9a-z\-]+/locations/.*`

### bucket.location

The GCS Bucket Location

* **Type**: `string`
* **Required**: No, default: `"us"`

### bucket.logBucket

GCS Logging Bucket

* **Type**: `string`
* **Required**: No, default: 

### bucket.lifecycleRule

GCS lifecycleRules

* **Type**: `object` `[]`
* **Required**: No, default: `[]`

### bucket.versioning

Bucket Versioning Boolean

* **Type**: `boolean`
* **Required**: No, default: `false`

### bucket.gcp

* **Type**: `object`
* **Required**: No, default: `{}`




---------------------------------------
<a name="reference-topic"></a>
## Topic Schema

**`Topic Schema` Properties**

|   |Type|Description|Required|
|---|---|---|---|
|**name**|`string`|The topic name to create| &#10003; Yes|
|**kmsKey**|`string`|KMS Key self link to use.|No, default: |

Additional properties are allowed.

### topic.name

The topic name to create

* **Type**: `string`
* **Required**:  &#10003; Yes

### topic.kmsKey

KMS Key self link to use.

* **Type**: `string`
* **Required**: No, default: 
* **Pattern**: `^projects/[0-9a-z\-]+/locations/.*`


