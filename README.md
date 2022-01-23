# rabotaua/actions-grahpql

GitHub Action to persorm GraphQL checks

## Inputs

- `endpoint` **required** - url to graphql where schema can be retrieved, make sure that this is url to graphql rather than playground or home page
- `service` **required** - name of the service in graph
- `key` **required** - key for apollo studio
- `token` **required** - github token with read access

## Example usage

```yml
- uses: rabotaua/actions-graphql@main
  with:
    endpoint: http://localhost:5000/graphql
    service: vacancies
    token: ${{ secrets.GH_TOKEN }}
    key: ${{ secrets.APOLLO_KEY }}
```
