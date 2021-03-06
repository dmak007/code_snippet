###### prop-types 설치

```bash
$ yarn add prop-types
```

<br>

###### prop-types 설정

- MoviePresenter.js

```react
import React from 'react';
import PropTypes from 'prop-types';

const MoviePresenter = ({
  loading,
  trending,
  nowPlaying,
  topRated,
  upcoming,
  error
}) => 'Movies Area';

MoviePresenter.propTypes = {
  loading: PropTypes.bool.isRequired,
  trending: PropTypes.array,
  nowPlaying: PropTypes.array,
  topRated: PropTypes.array,
  upcoming: PropTypes.array,
  error: PropTypes.string
};

export default MoviePresenter;
```

- TVPresenter.js

```react
import React from 'react';
import PropTypes from 'prop-types';

const TVPresenter = ({
  loading,
  trending,
  onTheAir,
  popular,
  topRated,
  error
}) => 'TV Shows Area';

TVPresenter.propTypes = {
  loading: PropTypes.bool.isRequired,
  trending: PropTypes.array,
  onTheAir: PropTypes.array,
  popular: PropTypes.array,
  topRated: PropTypes.array,
  error: PropTypes.string
};

export default TVPresenter;
```

- SearchPresenter.js

```react
import React from 'react';
import PropTypes from 'prop-types';

const SearchPresenter = ({
  loading,
  searchWord,
  movieResults,
  tvResults,
  error,
  handleSubmit
}) => 'Search Input & Results Area';

SearchPresenter.propTypes = {
  loading: PropTypes.bool.isRequired,
  searchWord: PropTypes.string,
  movieResults: PropTypes.array,
  tvResults: PropTypes.array,
  error: PropTypes.string,
  handleSubmit: PropTypes.func.isRequired
};

export default SearchPresenter;
```

- DetailPresenter.js

```react
import React from 'react';
import PropTypes from 'prop-types';

const DetailPresenter = ({ loading, result, error }) => 'Each Detail Area';

DetailPresenter.propTypes = {
  loading: PropTypes.bool.isRequired,
  result: PropTypes.object,
  error: PropTypes.string
};

export default DetailPresenter;
```

> `detailResult: PropTypes.object`에 주의

<br>

<br>

###### Commit

```bash
$ git add .
$ git commit -m 'Set PropTypes'
$ git push origin master
```

<br>

<br>