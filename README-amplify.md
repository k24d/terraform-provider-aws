# Amplify resources for terraform-provider-aws

## Prerequisite

Install Go language.  On macOS, you can use Homebrew:

```
$ brew install go
```

## Build and install

Checkout repositories:

```
# origin
git clone https://github.com/terraform-providers/terraform-provider-aws.git

cd terraform-provider-aws

# branches
git remote add amplify https://github.com/k24d/terraform-provider-aws.git
git fetch amplify
```

Merge branches:

```
# use the latest release
VERSION=v2.61.0
git reset --hard $VERSION

# create a working branch
git checkout -b amplify

# merge branches
git merge amplify/f-amplify-app -m "Merge remote-tracking branch 'amplify/f-amplify-app' into amplify"
git merge amplify/f-amplify-backend-environment -m "Merge remote-tracking branch 'amplify/f-backend-environment' into amplify"
git merge amplify/f-amplify-branch -m "Merge remote-tracking branch 'amplify/f-amplify-branch' into amplify"
git merge amplify/f-amplify-domain-association -m "Merge remote-tracking branch 'amplify/f-amplify-domain-association' into amplify"
git merge amplify/f-amplify-webhook -m "Merge remote-tracking branch 'amplify/f-amplify-webhook' into amplify"
```

Build a binary:

```
go install
```

Copy the binary to your plugin directory:

```
VERSION=v2.61.0
cp ~/go/bin/terraform-provider-aws ~/.terraform.d/plugins/terraform-provider-aws_${VERSION}_x4
```

## Configuration

Set aws provider in your main.tf and run `terraform init`:

```
provider "aws" {
  version = "~> 2.61"
}
```

## Documentation

- [Amplify App](https://github.com/k24d/terraform-provider-aws/blob/f-amplify-app/website/docs/r/amplify_app.html.markdown)
- [Amplify Backend Environment](https://github.com/k24d/terraform-provider-aws/blob/f-amplify-backend-environment/website/docs/r/amplify_backend_environment.html.markdown)
- [Amplify Branch](https://github.com/k24d/terraform-provider-aws/blob/f-amplify-branch/website/docs/r/amplify_branch.html.markdown)
- [Amplify Domain Association](https://github.com/k24d/terraform-provider-aws/blob/f-amplify-domain-association/website/docs/r/amplify_domain_association.html.markdown)
- [Amplify Webhook](https://github.com/k24d/terraform-provider-aws/blob/f-amplify-webhook/website/docs/r/amplify_webhook.html.markdown)
