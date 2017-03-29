# react-redux-snippets
React and Redux Snippets for the future with ES6 and ES7 capabiilities

## Redux Snippets

#### Action Type - `act-t`

```javascript
export const ${1:ACTION_TYPE} = 'app/${2: reducer}/${1:ACTION_TYPE}'
```

#### Action Creators File - `act-f`
```javascript
/**
 * Action Creators for ${1: Reducer} reducer
**/

import ${2:ACTION_TYPE} from './constants';

export function ${3: actionCreatorName} (${4:payload}) {
    return {
        type: ${2:ACTION_TYPE},
        ${4:payload}
    }
}
```

#### Action Creator - `act-c`
```javascript
export function ${1: actionCreatorName} (${3:payload}) {
    return {
        type: ${2:ACTION_TYPE},
        ${3:payload}
    }
}
```

#### Redux Reducer File - `red-f`
```javascript
  /**
   *  ${1:reducerName} reducer
   */
  import { fromJS } from 'immutable';

  // Import Action Types
  import { ${2:ACTION_TYPE} } from './constants';

  const initialState = fromJS({
    ${3:key}: ${4:value}
  });

  function ${1:reducerName}(state = initialState, action) {
    switch (action.type) {
      case ${2:ACTION_TYPE}:
        return state;
      default:
        return state;
    }
  }

  export default ${1:ComponentName};

  ```
## React Component Snippets
#### React Component  - `rcc`

  ```javascript
  import React, { Component, PropTypes } from 'react';

  /**
   * ${1:ComponentName}
   */
  export class ${1:ComponentName} extends Component { // eslint-disable-line react/prefer-stateless-function
    render() {
      return (
        <div>MY COMPONENT</div>
      );
    }
  }

  ${1:ComponentName}.propTypes = {
    ${2:prop}: PropTypes.${3:type}.isRequired
  }

  export default ${1:ComponentName};
  ```

## Styled Components
#### Styled Component - `sc`

```javascript
const ${1:ComponentName} = styled.${2:div}`
  $3
`;
```

#### Styled Component Export - `sc-e`
```javascript
export const ${1:ComponentName} = styled.${2:div}`
  $3
`;
```

#### Styled Components Import - `sc-i`
```javascript
import styled from 'styled-component';
```

## Redux Saga Snippets

#### Saga File - `saga-f`
```javascript
/**
 * ${1:defaultSagaName} Saga
 */

// Import Global Dependencies
import { takeLatest, take, put, cancel } from 'redux-saga/effects';
import { LOCATION_CHANGE } from 'react-router-redux';

// Import Local Dependencies
import { ${3:ACTION_TYPE} } from './constants';

export function* ${2:calledSaga}() {

}

export function* ${1:defaultSagaName}() {
  const watcher = yield takeLatest(${3:ACTION_TYPE}, ${2:calledSaga});
  yield take(LOCATION_CHANGE);
  yield cancel(watcher);
}

export default [${1:defaultSagaName}];
```

#### Saga Form Submit File - `saga-form`
```javascript
/**
 * ${1:defaultSagaName} Saga
 */

// Import Global Dependencies
import { takeLatest, take, put, call, cancel } from 'redux-saga/effects';
import { LOCATION_CHANGE } from 'react-router-redux';
import { startSubmit, stopSubmit, reset } from 'redux-form/immutable';
import api from '${2:utils/api}';

// Import Local Dependencies
import { ${3:ACTION_TYPE} } from './constants';

export function* ${4:calledSaga}(action) {
  const data = action.${5:data};
  const formId = action.formId;
  yield put(startSubmit(formId));
  try {
    const response = yield call(api, '${6:method}', '${7:/endpoint}', {
      data
    });
    console.log(response);
    yield put(stopSubmit(formId));
    yield put(reset(formId));
  } catch (error) {
    console.error(error);
    yield put(stopSubmit(formId, { _error: error}));
  }
}

export function* ${1:defaultSagaName}() {
  const watcher = yield takeLatest(${3:ACTION_TYPE}, ${4:calledSaga});
  yield take(LOCATION_CHANGE);
  yield cancel(watcher);
}

export default [${1:defaultSagaName}];
```

#### Saga api call - `saga-a`

```javascript
try {
  const response = yield call(api, '${1:method}', '${2:/endpoint}', {
    data
  });
  console.log(response);
  $3
} catch (error) {
  console.error(error);
}
```
