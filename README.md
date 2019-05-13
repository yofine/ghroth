# Artemis
Artemis allows you to fetch data from your REST-API and provides Apollo-like Query & Mutation.

## Installation
```
npm i -S 'artemis-react'
```
## Usage

```
import { ArtemisClient, ArtemisProvider } from 'artemis-react'

const client = ArtemisClient()
ReactDOM.render(
  <ArtemisProvider client={client}>
    <MyRootComponent />
  </ArtemisProvider>,
  document.getElementById('root'),
)
```


### render prop
```
import { Query } from 'artemis-react'

const GET_POSTS = async () => {
  const posts = await fetch('/posts')
  return posts
}

const Posts = () => (
  <Query query={GET_POSTS}>
	    {({ loading, error, data })} => {
	      if (error) return `Error! ${error.message}`
	      return (
	        <Table 
	          loading={loading}
	          dataSource={data}
	          columns={[...]}
	        />
	      )
	    }	    
  </Query>
)
```

### react hooks
```
import { useQuery } from 'artemis-react'

const GET_POSTS = async () => {
  const posts = await fetch('/posts')
  return posts
}

const Posts = () => {
  const { loading, error, data } = useQuery(GET_POSTS)
  if (error) return `Error! ${error.message}`
  return (
    <Table
	    loading={loading}
	    dataSource={data}
	    columns={[...]}
    />
  )
}
```
