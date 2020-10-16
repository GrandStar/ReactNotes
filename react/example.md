# Example

todo list:



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



