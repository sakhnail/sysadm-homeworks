1. Все перечисленные resource: https://github.com/hashicorp/terraform-provider-aws/blob/4063920637253c649b6369438d3503c358b06e56/internal/provider/provider.go#L717

Все перечисленные data_source: https://github.com/hashicorp/terraform-provider-aws/blob/4063920637253c649b6369438d3503c358b06e56/internal/provider/provider.go#L340

2. Строчка кода с конфликтующим <code>name</code> [ConflictsWith: []string{"name_prefix"},](https://github.com/hashicorp/terraform-provider-aws/blob/8e4d8a3f3f781b83f96217c2275f541c893fec5a/aws/resource_aws_sqs_queue.go#L56)

* Длина строки не более 80 символов: https://github.com/hashicorp/terraform-provider-aws/blob/8e4d8a3f3f781b83f96217c2275f541c893fec5a/aws/validators.go#L1035
* Регулярное выражение, которому подчиняется <code>name</code> 
```shell
if !regexp.MustCompile(`^[0-9A-Za-z-_]+(\.fifo)?$`).MatchString(value) {
		errors = append(errors, fmt.Errorf("only alphanumeric characters and hyphens allowed in %q", k))
```