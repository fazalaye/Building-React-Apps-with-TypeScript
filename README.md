# Building-React-Apps-with-TypeScript
Solution for Converting React Components to TypeScript
Step-by-Step Approach:
Define TypeScript Interfaces/Type Annotations:

For functional components: Create an interface for props.

For class components: Define interfaces for props and state.

Add Explicit Typings:

Annotate function parameters and state objects.

Use generics with Component for class components.

Handle Event Types:

Type event handlers (e.g., React.MouseEvent).

Leverage TypeScript Features:

Use strict type checking to catch errors early.

Code 01: Functional Component (Greeting.tsx)

import React from 'react';

// Define interface for component props
interface GreetingProps {
  name: string; // 'name' must be a string
}

// Functional component with typed props
const Greeting: React.FC<GreetingProps> = ({ name }) => {
  return <div>Hello, {name}!</div>;
};

export default Greeting;


Code 02: Class Component (Counter.tsx)

import React, { Component } from 'react';

// Define interfaces for props and state
interface CounterProps {} // Empty since no props are used
interface CounterState {
  count: number; // 'count' must be a number
}

class Counter extends Component<CounterProps, CounterState> {
  // Initialize state with explicit type
  state: CounterState = {
    count: 0,
  };

  // Typed event handler
  increment = (): void => {
    this.setState((prevState) => ({
      count: prevState.count + 1,
    }));
  };

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        {/* onClick expects a MouseEvent handler */}
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}

export default Counter;
