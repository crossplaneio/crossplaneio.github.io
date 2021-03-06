# cache.azure.crossplane.io/v1alpha2 API Reference

Package v1alpha2 contains managed resources for Azure cache services such as Redis.

This API group contains the following Crossplane resources:

* [Redis](#Redis)
* [RedisClass](#RedisClass)

## Redis

A Redis is a managed resource that represents an Azure Redis cluster.


Name | Type | Description
-----|------|------------
`apiVersion` | string | `cache.azure.crossplane.io/v1alpha2`
`kind` | string | `Redis`
`metadata` | [meta/v1.ObjectMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.15/#objectmeta-v1-meta) | Kubernetes object metadata.
`spec` | [RedisSpec](#RedisSpec) | A RedisSpec defines the desired state of a Redis.
`status` | [RedisStatus](#RedisStatus) | A RedisStatus represents the observed state of a Redis.



## RedisClass

A RedisClass is a non-portable resource class. It defines the desired spec of resource claims that use it to dynamically provision a managed resource.


Name | Type | Description
-----|------|------------
`apiVersion` | string | `cache.azure.crossplane.io/v1alpha2`
`kind` | string | `RedisClass`
`metadata` | [meta/v1.ObjectMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.15/#objectmeta-v1-meta) | Kubernetes object metadata.
`specTemplate` | [RedisClassSpecTemplate](#RedisClassSpecTemplate) | SpecTemplate is a template for the spec of a dynamically provisioned Redis.



## RedisClassSpecTemplate

A RedisClassSpecTemplate is a template for the spec of a dynamically provisioned Redis.

Appears in:

* [RedisClass](#RedisClass)




RedisClassSpecTemplate supports all fields of:

* [v1alpha1.NonPortableClassSpecTemplate](../crossplane-runtime/core-crossplane-io-v1alpha1.md#nonportableclassspectemplate)
* [RedisParameters](#RedisParameters)


## RedisParameters

RedisParameters define the desired state of an Azure Redis cluster. Most fields map directly to an Azure Redis resource: https://docs.microsoft.com/en-us/rest/api/redis/redis/create#redisresource

Appears in:

* [RedisClassSpecTemplate](#RedisClassSpecTemplate)
* [RedisSpec](#RedisSpec)


Name | Type | Description
-----|------|------------
`resourceGroupName` | string | ResourceGroupName in which to create this resource.
`location` | string | Location in which to create this resource.
`sku` | [SKUSpec](#SKUSpec) | SKU of the Redis cache to deploy.
`enableNonSslPort` | Optional bool | EnableNonSSLPort specifies whether the non-ssl Redis server port (6379) is enabled.
`shardCount` | Optional int | ShardCount specifies the number of shards to be created on a Premium Cluster Cache.
`staticIP` | Optional string | StaticIP address. Required when deploying a Redis cache inside an existing Azure Virtual Network.
`subnetId` | Optional string | SubnetID specifies the full resource ID of a subnet in a virtual network to deploy the Redis cache in. Example format: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/Microsoft.{Network|ClassicNetwork}/VirtualNetworks/vnet1/subnets/subnet1
`redisConfiguration` | Optional map[string]string | RedisConfiguration specifies Redis Settings.



## RedisSpec

A RedisSpec defines the desired state of a Redis.

Appears in:

* [Redis](#Redis)




RedisSpec supports all fields of:

* [v1alpha1.ResourceSpec](../crossplane-runtime/core-crossplane-io-v1alpha1.md#resourcespec)
* [RedisParameters](#RedisParameters)


## RedisStatus

A RedisStatus represents the observed state of a Redis.

Appears in:

* [Redis](#Redis)


Name | Type | Description
-----|------|------------
`state` | string | State represents the state of an Azure Redis.
`providerID` | string | ProviderID is the external ID to identify this resource in the cloud provider.
`endpoint` | string | Endpoint of the Redis resource used in connection strings.
`port` | int | Port at which the Redis endpoint is listening.
`sslPort` | int | SSLPort at which the Redis endpoint is listening.
`redisVersion` | string | RedisVersion the Redis endpoint is running.
`resourceName` | string | ResourceName of the Redis cache resource.


RedisStatus supports all fields of:

* [v1alpha1.ResourceStatus](../crossplane-runtime/core-crossplane-io-v1alpha1.md#resourcestatus)


## SKUSpec

An SKUSpec represents the performance and cost oriented properties of a Redis.

Appears in:

* [RedisParameters](#RedisParameters)


Name | Type | Description
-----|------|------------
`name` | string | Name specifies what type of Redis cache to deploy. Valid values: (Basic, Standard, Premium). Possible values include: &#39;Basic&#39;, &#39;Standard&#39;, &#39;Premium&#39;
`family` | string | Family specifies which family to use. Valid values: (C, P). Possible values include: &#39;C&#39;, &#39;P&#39;
`capacity` | int | Capacity specifies the size of Redis cache to deploy. Valid values: for C family (0, 1, 2, 3, 4, 5, 6), for P family (1, 2, 3, 4).



This API documentation was generated by `crossdocs`.