# format

Tools for working with the output of commands in Cog pipelines.

## Commands

* `format:head` - filter the output to only include the first N responses
* `format:fields` - show the keys included in a command response
* `format:list` - build a list of the values for a given key from each response object
* `format:table` - format command response as a table. see-also: `operable:table`
* `format:tail` - filter the output to only include the last N responses

## Permissions

 * None. All commands are set to `allow` by default.

## Examples

All of the examples below will use the following seed as input. This seed command is shortened to `seed ...` in the examples for the sake of brevity.
```
seed '[{ "name": "geddy", "role": "lead singer/bass guitar" },{ "name": "neil", "role": "drummer/lyricist" }, { "name": "alex", "role": "lead guitar" }]'
```
-------------------------------------------------------------------------------
### format:head

```
> seed ... | format:head 1
```
```json
{
  "name": "geddy",
  "role": "lead singer/bass guitar"
}
```
-------------------------------------------------------------------------------
### format:fields
```
> seed ... | format:head 1 | format:fields
```
```
name role
```
-------------------------------------------------------------------------------
### format:list
```
> seed '[{ "name": "geddy", "role": [ "bass guitar", "lead singer" ] },{ "name": "neil", "role": [ "drummer", "lyricist" ]}, { "name": "alex", "role": [ "lead guitar" ] }]' | format:list name
```
```
alex, geddy, neil
```
-------------------------------------------------------------------------------
### format:table

```
> seed ... | format:table name role
```
```
+-------+-------------------------+
| name  |          role           |
+-------+-------------------------+
| geddy | lead singer/bass guitar |
| neil  | drummer/lyricist        |
| alex  | lead guitar             |
+-------+-------------------------+
```
-------------------------------------------------------------------------------
### format:head

```
> seed ... | format:tail 1
```
```json
{
  "name": "alex",
  "role": "lead guitar"
}
```
-------------------------------------------------------------------------------

## License

[Apache 2](https://github.com/cogcmd/format/blog/master/LICENSE)
