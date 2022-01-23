# rabotaua/actions-grahpql

GitHub Action to persorm GraphQL checks

## Inputs

- `endpoint` **required** - url to graphql where schema can be retrieved, make sure that this is url to graphql rather than playground or home page
- `service` **required** - name of the service in graph
- `key` **required** - key for apollo studio
- `token` **required** - github token with read access

## Example usage

Chain:
- docker build
- docker run
- graphql action
- docker push

```yml
- name: docker build
  run: docker build -t $IMAGE .

- name: docker run
  run: docker run -d --name=service -p 5000:80 $IMAGE


# Put me between `docker build` and `docker push`
- uses: rabotaua/actions-graphql@main
  with:
    endpoint: http://localhost:5000/graphql
    service: vacancies
    token: ${{ secrets.GH_TOKEN }}
    key: ${{ secrets.APOLLO_KEY }}


- name: docker logs
  if: always()
  run: docker logs service

- name: docker rm
  if: always()
  run: docker rm -f service

- name: docker push
  run: docker push $IMAGE:$VERSION
```
