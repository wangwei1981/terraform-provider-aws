---
subcategory: "Lambda"
layout: "aws"
page_title: "AWS: aws_lambda_code_signing_config"
description: |-
  Provides a Lambda Code Signing Config resource.
---


<!-- Please do not edit this file, it is generated. -->
# Resource: aws_lambda_code_signing_config

Provides a Lambda Code Signing Config resource. A code signing configuration defines a list of allowed signing profiles and defines the code-signing validation policy (action to be taken if deployment validation checks fail).

For information about Lambda code signing configurations and how to use them, see [configuring code signing for Lambda functions][1]

## Example Usage

```typescript
// Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { TerraformStack } from "cdktf";
/*
 * Provider bindings are generated by running `cdktf get`.
 * See https://cdk.tf/provider-generation for more details.
 */
import { LambdaCodeSigningConfig } from "./.gen/providers/aws/lambda-code-signing-config";
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string) {
    super(scope, name);
    new LambdaCodeSigningConfig(this, "new_csc", {
      allowedPublishers: {
        signingProfileVersionArns: [example1.arn, example2.arn],
      },
      description: "My awesome code signing config.",
      policies: {
        untrustedArtifactOnDeployment: "Warn",
      },
    });
  }
}

```

## Argument Reference

* `allowedPublishers` (Required) A configuration block of allowed publishers as signing profiles for this code signing configuration. Detailed below.
* `policies` (Optional) A configuration block of code signing policies that define the actions to take if the validation checks fail. Detailed below.
* `description` - (Optional) Descriptive name for this code signing configuration.

The `allowedPublishers` block supports the following argument:

* `signingProfileVersionArns` - (Required) The Amazon Resource Name (ARN) for each of the signing profiles. A signing profile defines a trusted user who can sign a code package.

The `policies` block supports the following argument:

* `untrustedArtifactOnDeployment` - (Required) Code signing configuration policy for deployment validation failure. If you set the policy to Enforce, Lambda blocks the deployment request if code-signing validation checks fail. If you set the policy to Warn, Lambda allows the deployment and creates a CloudWatch log. Valid values: `warn`, `enforce`. Default value: `warn`.

## Attributes Reference

In addition to all arguments above, the following attributes are exported:

* `arn` - The Amazon Resource Name (ARN) of the code signing configuration.
* `configId` - Unique identifier for the code signing configuration.
* `lastModified` - The date and time that the code signing configuration was last modified.

[1]: https://docs.aws.amazon.com/lambda/latest/dg/configuration-codesigning.html

## Import

Code Signing Configs can be imported using their ARN, e.g.,

```
$ terraform import aws_lambda_code_signing_config.imported_csc arn:aws:lambda:us-west-2:123456789012:code-signing-config:csc-0f6c334abcdea4d8b
```

<!-- cache-key: cdktf-0.17.1 input-6c61d4ccf01736732c1c402734d9063a75bd7b54df656a8859ad6d209a197851 -->