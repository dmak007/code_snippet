## Set Router

1. Route 설정 (`Container & Presenter` pattern 사용)
2. Router 설정 (각 Route 컴포넌트 연결)
3. App 컴포넌트에서 import

<br>

<br>

#### `Container & Presenter` Pattern

1. `Container`
   - Write Logic
   - state 관리, API 호출 등의 로직 처리
2. `Presenter`
   - Only UI
   - stateless, prop-types 설정

<br>

<br>

#### Route 설정

###### 디렉토리 생성

```bash
$ cd src
$ mkdir routes
```

<br>

###### 디렉토리 생성

```bash
$ cd routes
$ mkdir Movie
$ mkdir TV
$ mkdir Search
$ mkdir Detail
```

<br>

###### 파일 생성: `index` / `Container` / `Presenter`

- Movie

```bash
$ cd Movie
$ touch index.js
$ touch MovieContainer.js
$ touch MoviePresenter.js
```

- TV

```bash
$ cd ..
$ cd TV
$ touch index.js
$ touch TVContainer.js
$ touch TVPresenter.js
```

- Search

```bash
$ cd ..
$ cd Search
$ touch index.js
$ touch SearchContainer.js
$ touch SearchPresenter.js
```

- Detail

```bash
$ cd ..
$ cd Detail
$ touch index.js
$ touch DetailContainer.js
$ touch DetailPresenter.js
```

<br>

###### 코드 작성: `Presenter`

- MoviePresenter.js

```react
export default () => 'Movies Area';
```

- TVPresenter.js

```react
export default () => 'TV Shows Area';
```

- SearchPresenter.js

```react
export default () => 'Search Input & Results Area';
```

- DetailPresenter.js

```react
export default () => 'Each Detail Area';
```

<br>

###### 코드 작성: `Container`

- MovieContainer.js

```react
import React from 'react';
import MoviePresenter from './MoviePresenter';

export default class extends React.Component {
  render() {
    return <MoviePresenter />;
  }
}
```

- TVContainer.js

```react
import React from 'react';
import TVPresenter from './TVPresenter';

export default class extends React.Component {
  render() {
    return <TVPresenter />;
  }
}
```

- SearchContainer.js

```react
import React from 'react';
import SearchPresenter from './SearchPresenter';

export default class extends React.Component {
  render() {
    return <SearchPresenter />;
  }
}
```

<br>

- DetailContainer.js

```react
import React from 'react';
import DetailPresenter from './DetailPresenter';

export default class extends React.Component {
  render() {
    return <DetailPresenter />;
  }
}
```

<br>

###### 코드 작성: `index`

- Movie/index.js

```react
import MovieContainer from './MovieContainer';

export default MovieContainer;
```

- TV/index.js

```react
import TVContainer from './TVContainer';

export default TVContainer;
```

- Search/index.js

```react
import SearchContainer from './SearchContainer';

export default SearchContainer;
```

- Detail/index.js

```react
import DetailContainer from './DetailContainer';

export default DetailContainer;
```

<br>

<br>

#### Router 설정

###### react-router-dom 설치

```bash
$ yarn add react-router-dom
```

<br>

###### 컴포넌트 생성

```bash
$ cd src
$ cd components
$ touch Router.js
```

<br>

###### 코드 작성

- Router.js

```react
import React from 'react';
import {
  BrowserRouter as Router,
  Route,
  Switch,
  Redirect
} from 'react-router-dom';
import Movie from 'routes/Movie';
import TV from 'routes/TV';
import Search from 'routes/Search';
import Detail from 'routes/Detail';

export default () => (
  <Router>
    <Switch>
      <Route path="/" exact component={Movie} />
      <Route path="/tv" component={TV} />
      <Route path="/search" component={Search} />
      <Route path="/movie/:id" component={Detail} />
      <Route path="/show/:id" component={Detail} />
      <Redirect from="*" to="/" />
    </Switch>
  </Router>
);
```

<br>

#### Import

- App.js

```react
...
import Router from './Router';

class App extends Component {
  render() {
    return (
      <React.Fragment>
        <Router />
        <GlobalStyle />
      </React.Fragment>
    );
  }
}

...
```

> `localhost:3000`: Movies Area
>
> `localhost:3000/tv`: TV Shows Area
>
> `localhost:3000/search`: Search Input & Results Area
>
> `localhost:3000/movie/272`: Each Detail Area
>
> `localhost:3000/show272`: Each Detail Area
>
> `localhost:3000/abc`: `/`로 Redirect

<br>

<br>

###### Commit

```bash
$ git add .
$ git commit -m 'Set Router'
$ git push origin master
```

<br>

<br>