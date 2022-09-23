Terraform Honeycomb Buildevents Starter Pack
============================================

This module creates resources like Boards and Queries in [Honeycomb](https://www.honeycomb.io) to kick off exploration
of [Build events](https://github.com/honeycombio/buildevents) sent by CI/CD systems.

## Use

The minimal config is:
```hcl
module "explore-buildevents" {
  source = "honeycombio/buildevents-starter-pack/honeycombio"

  honeycomb_dataset = "buildevents" # Optional: defaults to buildevents
  query_time_range = 604800 # in seconds. Optional: defaults to 7 days
  ideal_build_duration_ms = 120000 # in milliseconds. Optional: defaults to 2 minutes
}
```
Set the API key used by Terraform setting the HONEYCOMB_API_KEY environment variable.
```bash
export HONEYCOMB_API_KEY=$HONEYCOMB_API_KEY
```

Now you can run `terraform plan/apply` in sequence.

For more config options, see [USAGE.md](https://github.com/honeycombio/terraform-honeycombio-buildevents-starter-pack/blob/main/USAGE.md).

## Examples

Examples of use of this module can be found in [`examples/`](https://github.com/honeycombio/terraform-honeycombio-buildevents-starter-pack/tree/main/examples).  We've
provided a build durations exploration example.

## Development

### Tests
Test cases that run against local code are in [`examples/`](https://github.com/honeycombio/terraform-honeycombio-buildevents-starter-pack/tree/main/examples). To set up:

1. Set the API key used by Terraform setting the HONEYCOMB_API_KEY environment variable.

3. `terraform plan` and `terraform apply` will now work as expected, as will
   `terraform destroy`.

4. Test cases also run as part of the pipeline. See [test-terraform-module.yml](https://github.com/honeycombio/terraform-honeycombio-buildevents-starter-pack/blob/main/.github/workflows/test-terraform-module.yml)

### Docs
Docs are autogenerated via `./docs.sh`, and put in [USAGE.md](https://github.com/honeycombio/terraform-honeycombio-buildevents-starter-pack/blob/main/USAGE.md).  Please
regenerate and commit before merging.

### Lints
We use [tflint](https://github.com/terraform-linters/tflint) and `terraform
fmt`, and enforce this with a [github action](.github/workflows/tflint.yml).


## Contributions
Features, bug fixes and other changes to this module are gladly accepted. Please open issues or a pull request with your change.

All contributions will be released under the Apache License 2.0.
