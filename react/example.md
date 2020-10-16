# Example

## 

## todo list:



```text
import React, {Component} from "react";

export default class App extends Component {
  constructor(props) {
    super(props);
    this.state = {
      newItem: "",
      list: []
    }

    this.inputChange = this.inputChange.bind(this);
    this.handleOnClick = this.handleOnClick.bind(this);
    this.deleteItem = this.deleteItem.bind(this);

  }
  render() {
    return (
      <div className="App">
        <h1>Todo list</h1>
       <input type="text" value={this.state.newItem} onChange={e => this.inputChange(e.target.value)}>
       </input>
       <button onClick={this.handleOnClick}>
          add
         </button>

         {this.state.list.map((ele) => {
           return (
             <ul>
               <div key={ele.id}>
                  {ele.value}
                <button onClick={() => this.deleteItem(ele)}>
                      delete
                </button>
                </div>
              </ul>
           )
          })}
      </div>
    );
  }

  inputChange(e) {
    this.setState({
      newItem: e
    })
  }
  
  deleteItem(ele) {
    const updated = this.state.list.filter(item => item.id !== ele.id);
    console.log(updated);
    this.setState({
      list: updated
    })
  }

  handleOnClick() {
    if(this.state.newItem === "") return;
    const newItem = {
      value: this.state.newItem,
      id: 1 + Math.random()
    }
    this.setState({
      list: [...this.state.list, newItem],
      newItem: ""
    })
  }
}

```

## Todo2





```text
import React, { Component } from 'react';
import List from '../List';
import CreateItem from '../CreateItem';
import Filter from '../Filter';

import './style.css';

class App extends Component {
  constructor(props) {
    super(props);
    this.state = {
      data: [],
      filter: 'all'
    };
  }

  createTodo = text => {
    if (text.trim() !== '') {
      this.setState({
        data: [...this.state.data, { text: text, completed: false }]
      });
    }
  };

  toggleTodo = id => {
    const currentTodo = this.state.data[id];
    const newTodo = { ...currentTodo, completed: !currentTodo.completed };

    this.setState({
      data: [
        ...this.state.data.slice(0, id),
        newTodo,
        ...this.state.data.slice(id + 1)
      ]
    });
  };

  setFilter = filter => {
    this.setState({ filter: filter });
  };

  render() {
    console.log(this.state);
    return (
      <div className="App">
        <CreateItem createTodo={this.createTodo} />
        <List
          list={this.state.data}
          toggleTodo={this.toggleTodo}
          currentFilter={this.state.filter}
        />
        <Filter currentFilter={this.state.filter} setFilter={this.setFilter} />
      </div>
    );
  }
}

export default App;


import React from 'react';

import './style.css';

class CreateItem extends React.Component {
  constructor(props) {
    super(props);
    this.state = { input: '' };
  }

  onInputChange = e => {
    this.setState({ input: e.target.value });
  };

  onCreateItem = () => {
    this.props.createTodo(this.state.input);
    this.setState({ input: '' });
  };
  render() {
    return (
      <div className="CreateItem">
        <input
          className="CreateItem-input"
          onChange={this.onInputChange}
          value={this.state.input}
        />
        <button className="CreateItem-button" onClick={this.onCreateItem}>
          Create
        </button>
      </div>
    );
  }
}

export default CreateItem;


import React from 'react';
import './style.css';

const Filter = props => {
  return (
    <div className="Filter">
      <button
        className="Filter-button"
        onClick={() => {
          props.setFilter('all');
        }}
        disabled={props.currentFilter === 'all'}
      >
        All
      </button>
      <button
        className="Filter-button"
        onClick={() => {
          props.setFilter('completed');
        }}
        disabled={props.currentFilter === 'completed'}
      >
        Completed
      </button>
      <button
        className="Filter-button"
        onClick={() => {
          props.setFilter('active');
        }}
        disabled={props.currentFilter === 'active'}
      >
        Active
      </button>
    </div>
  );
};

export default Filter;


import React from 'react';
import './style.css';
const List = props => {
  const { list } = props;
  return (
    <ul className="List">
      {list.map((item, index) => {
        if (shouldShow(props.currentFilter, item.completed)) {
          return (
            <li
              className="List-item"
              key={index}
              onClick={() => {
                props.toggleTodo(index);
              }}
              style={{
                textDecoration: item.completed ? 'line-through' : 'none'
              }}
            >
              {item.text}
            </li>
          );
        } else {
          return null;
        }
      })}
    </ul>
  );
};

function shouldShow(currentFilter, completed) {
  if (currentFilter === 'all') {
    return true;
  } else if (currentFilter === 'completed' && completed) {
    return true;
  } else if (currentFilter === 'active' && !completed) {
    return true;
  } else {
    return false;
  }
}

export default List;
```

## Restaurant

```text
import React, { Component } from "react";
import ReactDOM from "react-dom";
import axios from "axios";
import SeletedDetail from "./SelectedDetail";
import "./styles.css";
import Categories from "./Categories";

class App extends Component {
  constructor(props) {
    super(props);
    this.state = { list: [], seletedDetail: [] };
  }
  componentDidMount() {
    console.log("res");
    axios({
      method: "get",
      url: "https://davids-restaurant.herokuapp.com/categories.json"
    })
      .then((res) => {
        console.log(res, "res");
        this.setState({ list: res.data });
      })
      .catch((err) => {
        console.log(err);
      });
  }
  handleClick = (id) => {
    axios({
      method: "get",
      url: `https://davids-restaurant.herokuapp.com/menu_items.json?category=${id}`
    })
      .then((res) => {
        this.setState({ seletedDetail: res.data });
      })
      .catch((err) => {
        console.log(err);
      });
  };

  render() {
    const { list, seletedDetail } = this.state;
    return (
      <div className="page">
        <div className="categories">
          <Categories
            key={this.id}
            list={list}
            handleClick={this.handleClick}
          />
        </div>
        <div className="details">
          <SeletedDetail data={seletedDetail} />
        </div>
      </div>
    );
  }
}

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);

```

Categories

```text
import React, { Component } from "react";
import "./styles.css";
class Categories extends Component {
  render() {
    const { list, handleClick } = this.props;
    return (
      <div className="category">
        <h1>Menu Categories</h1>
        <ul>
          {list.map(item => {
            return (
              <li onClick={() => handleClick(item.short_name)}>
                {`${item.name} -(${item.short_name})`}
              </li>
            );
          })}
        </ul>
      </div>
    );
  }
}
export default Categories;

```

selectedDetail

```text
import React, { Component } from "react";

class SeletedDetail extends Component {
  render() {
    const { category, menu_items } = this.props.data;
    return (
      <div>
        {category ? (
          <div>
            <h1>{`item in Category: (${category.short_name})`}</h1>
            <div>
              <table className="detailsTable">
                <tr>
                  <th>Name</th>
                  <th>Description</th>
                </tr>
                {menu_items.map((item, index) => {
                  return (
                    <tr>
                      <td>{item.name}</td>
                      <td>{item.description}</td>
                    </tr>
                  );
                })}
              </table>
            </div>
          </div>
        ) : null}
      </div>
    );
  }
}
export default SeletedDetail;

```

