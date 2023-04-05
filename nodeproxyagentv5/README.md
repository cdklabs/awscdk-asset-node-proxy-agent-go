# AWS Lambda Layer with the NPM dependency proxy-agent

<!--BEGIN STABILITY BANNER-->---


![cdk-constructs: Stable](https://img.shields.io/badge/cdk--constructs-stable-success.svg?style=for-the-badge)

---
<!--END STABILITY BANNER-->

This module bundles the NPM dependency [`proxy-agent`](https://www.npmjs.com/package/proxy-agent)
as a local asset. It exposes constants `ASSET_FILE` and `LAYER_SOURCE_DIR` that can be consumed
via the CDK `Asset` construct.

> * proxy-agent Version: 5.0.0

Usage:

```go
// Example automatically generated from non-compiling source. May contain errors.
import "github.com/aws-samples/dummy/awscdkassetnodeproxyagent"
import "github.com/aws/aws-cdk-go/awscdk"
import s3_assets "github.com/aws/aws-cdk-go/awscdk"
import "github.com/aws/aws-cdk-go/awscdk"

var fn function

asset := s3_assets.NewAsset(this, jsii.String("layer-asset"), &AssetProps{
	Path: awscdkassetnodeproxyagent.ASSET_FILE,
	AssetHash: awscdk.FileSystem_Fingerprint(*awscdkassetnodeproxyagent.LAYER_SOURCE_DIR),
})

fn.AddLayers(lambda.NewLayerVersion(this, jsii.String("ProxyAgentLayer"), &LayerVersionProps{
	Code: lambda.Code_FromBucket(asset.Bucket, asset.S3ObjectKey),
}))
```

[`proxy-agent`](https://www.npmjs.com/package/proxy-agent) will be installed under `/nodejs/node_modules`.
