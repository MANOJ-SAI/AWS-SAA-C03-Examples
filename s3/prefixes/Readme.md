
## Create the bucket
```sh
aws s3 mb s3://prefix-example-ms-01
```

## Create the folder

```sh
aws s3api put-object --bucket="prefix-example-ms-01" --key="hello/"
```

## Create the multiple folders

```sh
aws s3api put-object --bucket="prefix-example-ms-01" --key="Kafka/is/based/on/the/abstraction/of/a/distributed/commit/log./By/splitting/a/log/into/partitions,/Kafka/is/able/to/scale-out/systems./As/such,/Kafka/models/events/as/key/value/pairs./Internally,/keys/and/values/are/just/sequences/of/bytes,/but/externally/in/your/programming/language/of/choice,/they/are/often/structured/objects/represented/in/your/language’s/type/system./Kafka/famously/calls/the/translation/between/language/types/and/internal/bytes/serialization/and/deserialization"
```

## Try and break the 1024 limit
```sh
aws s3api put-object --bucket="prefix-example-ms-01" --key="Kafka/is/based/on/the/abstraction/of/a/distributed/commit/log./By/splitting/a/log/into/partitions,/Kafka/is/able/to/scale-out/systems./As/such,/Kafka/models/events/as/key/value/pairs./Internally,/keys/and/values/are/just/sequences/of/bytes,/but/externally/in/your/programming/language/of/choice,/they/are/often/structured/objects/represented/in/your/language’s/type/system./Kafka/famously/calls/the/translation/between/language/types/and/internal/bytes/serialization/and/deserialization./The/serialized/format/is/usually/JSON,/JSON/Schema,/Avro,/or/Protobuf/Values/are/typically/the/serialized/representation/of/an/application/domain/object/or/some/form/of/raw/message/input,/like/the/output/of/a/sensor/Keys/can/also/be/complex/domain/objects/but/are/often/primitive/types/like/strings/or/integers./The/key/part/of/a/Kafka/event/is/not/necessarily/a/unique/identifier/for/the/event,/like/the/primary/key/of/a/row/in/a/relational/database/would/be./It/is/more/likely/the/identifier/of/some/entity/in/the/system,/like/a/user,/order,/or/a/particular/connected/device/This/may/not/sound/so/significant/now,/but/we’ll/see/later/on/that/keys/are/crucial/for/how/Kafka/deals/with/things/like/parallelization/and/data/locality/"
```