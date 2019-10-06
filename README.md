# jnj-style-guide
This style guide is mostly based on the standards that are currently prevalent in JavaScript, although some conventions (i.e async/await or static class fields) may still be included or prohibited on a case-by-case basis. 

## Table of Contents

  1. [Basic Rules](#basic-rules)
  2. [Naming](#naming)
  3. [Alignment](#alignment)
  4. [Quotes](#quotes)
  5. [Spacing](#spacing)
  6. [Parentheses](#parentheses)
  7. [Tags](#tags)
  8. [Variables](#variables)
  9. [Props[(#props)

## Basic Rules

  - Follow DRY (Don’t repeat yourself), KISS (Keep it small and simple), DIE (Duplication Is Evil), YAGNI (You Ain’t Gonna Need It), SOLID principles
  - 
  
  
## Naming

  - **Extensions**: Use `.tsx` extension for React components with typescript.
  - **Filename**: Use PascalCase for filenames. E.g., `ReservationCard.tsx`. Class and components folders names must start with capital     letter.
  - **Reference Naming**: Use PascalCase for React components and camelCase for their instances.
  - **Component definition**: 

    All components (presentation, containers or pages) should **always** be
    defined as a directory, named with pascal casing. The main component file
    should be `index.js`, main stylesheet `style.css`. CSS custom properties
    can be kept in `properties.css`:

    ```
    ComponentName/
    ├── index.tsx
    └── styles.scss
    ```

    * Styles should always be defined in a separate SCSS file
    * Avoid prefixing or suffixing component names
      - E.g.: `lib/pages/UserPage` or `lib/container/UserContainer`
    * On conflict rename on import
      - `import UserContainer from '...'`
      - `import { User as UserContainer } from '...'`
  
## Alignment

  - Follow these alignment styles for JSX syntax.

    ```jsx
    // bad
    <Foo superLongParam="bar"
         anotherSuperLongParam="baz" />

    // good
    <Foo
      superLongParam="bar"
      anotherSuperLongParam="baz"
    />

    // if props fit in one line then keep it on the same line
    <Foo bar="bar" />

    // children get indented normally
    <Foo
      superLongParam="bar"
      anotherSuperLongParam="baz"
    >
      <Quux />
    </Foo>

    // bad
    {showButton &&
      <Button />
    }

    // bad
    {
      showButton &&
        <Button />
    }

    // good
    {showButton && (
      <Button />
    )}

    // good
    {showButton && <Button />}
    ```
    
    - One line props when there are more than 2 props

    Bad
    ```jsx
    <button type="submit" disabled onClick={() => {}} className="button">
      Click here
    </button>

    <button type="submit" className="button">
      Click here
    </button>

    <button className="aLongSpecificClassName">Click here</button>
    ```

    Good
    ```jsx
    <button
      className="button"
      disabled={loading}
      onClick={() => {}}
      type="submit"
    >
      Click here
    </button>
    ```

    - One line component
    Bad
    ``` js
    <div className="example"><span class="highlight">Bad</span> example</div>
    ```

    Good
    ``` js
    <div className="example">
      <span className="highlight">Bad</span>
      example
    </div>
    ```

    
    ## Quotes

  - Always use double quotes (`"`) for JSX attributes

    ```jsx
    // bad
    <Foo bar='bar' />

    // good
    <Foo bar="bar" />
    ```
    
    ## Spacing

  - Always include a single space in your self-closing tag.

    ```jsx
    // bad
    <Foo/>

    // very bad
    <Foo                 />

    // bad
    <Foo
     />

    // good
    <Foo />
    ```

## Parentheses

  - Wrap JSX tags in parentheses when they span more than one line.

    ```jsx
    // bad
    render() {
      return <MyComponent variant="long body" foo="bar">
               <MyChild />
             </MyComponent>;
    }

    // good
    render() {
      return (
        <MyComponent variant="long body" foo="bar">
          <MyChild />
        </MyComponent>
      );
    }

    // good, when single line
    render() {
      const body = <div>hello</div>;
      return <MyComponent>{body}</MyComponent>;
    }
    ```
    
    ## Tags

  - Always self-close tags that have no children.

    ```jsx
    // bad
    <Foo variant="stuff"></Foo>

    // good
    <Foo variant="stuff" />
    ```

  - If your component has multi-line properties, close its tag on a new line.

    ```jsx
    // bad
    <Foo
      bar="bar"
      baz="baz" />

    // good
    <Foo
      bar="bar"
      baz="baz"
    />
    ```
    
    ### Line length should not exceed 80 characters.

    
    ## Variables
    
   - Always define variables to increase
reuse and make styles more consistent.
```scss
$breakPoint-sm: 600px;
$breakPoint-md: 960px;
$breakPoint-lg: 1280px;
$breakPoint-xl: 1920px;
```
  ### Use explanatory variables


## Props

  - Always use camelCase for prop names.

    ```jsx
    // bad
    <Foo
      UserName="hello"
      phone_number={12345678}
    />

    // good
    <Foo
      userName="hello"
      phoneNumber={12345678}
    />
    ```

  - Omit the value of the prop when it is explicitly `true`.

    ```jsx
    // bad
    <Foo
      hidden={true}
    />

    // good
    <Foo
      hidden
    />

    // good
    <Foo hidden />
    ```

  - Always include an `alt` prop on `<img>` tags. If the image is presentational, `alt` can be an empty string or the `<img>` must have `role="presentation"`.

    ```jsx
    // bad
    <img src="hello.jpg" />

    // good
    <img src="hello.jpg" alt="Me waving hello" />

    // good
    <img src="hello.jpg" alt="" />

    // good
    <img src="hello.jpg" role="presentation" />
    ```

  - Do not use words like "image", "photo", or "picture" in `<img>` `alt` props.

    > Why? Screenreaders already announce `img` elements as images, so there is no need to include this information in the alt text.

    ```jsx
    // bad
    <img src="hello.jpg" alt="Picture of me waving hello" />

    // good
    <img src="hello.jpg" alt="Me waving hello" />
    ```

  - Use only valid, non-abstract

    ```jsx
    // bad - not an ARIA role
    <div role="datepicker" />

    // bad - abstract ARIA role
    <div role="range" />

    // good
    <div role="button" />
    ```

  - Do not use `accessKey` on elements.

  > Why? Inconsistencies between keyboard shortcuts and keyboard commands used by people using screenreaders and keyboards complicate accessibility.

  ```jsx
  // bad
  <div accessKey="h" />

  // good
  <div />
  ```

  - Avoid using an array index as `key` prop, prefer a stable ID. 

> Why? Not using a stable ID [is an anti-pattern](https://medium.com/@robinpokorny/index-as-a-key-is-an-anti-pattern-e0349aece318) because it can negatively impact performance and cause issues with component state.

We don’t recommend using indexes for keys if the order of items may change.

  ```jsx
  // bad
  {todos.map((todo, index) =>
    <Todo
      {...todo}
      key={index}
    />
  )}

  // good
  {todos.map(todo => (
    <Todo
      {...todo}
      key={todo.id}
    />
  ))}
  ```

  - Always define explicit defaultProps for all non-required props.

  > Why? propTypes are a form of documentation, and providing defaultProps means the reader of your code doesn’t have to assume as much. In addition, it can mean that your code can omit certain type checks.

  ```jsx
  // bad
  function SFC({ foo, bar, children }) {
    return <div>{foo}{bar}{children}</div>;
  }
  SFC.propTypes = {
    foo: PropTypes.number.isRequired,
    bar: PropTypes.string,
    children: PropTypes.node,
  };

  // good
  function SFC({ foo, bar, children }) {
    return <div>{foo}{bar}{children}</div>;
  }
  SFC.propTypes = {
    foo: PropTypes.number.isRequired,
    bar: PropTypes.string,
    children: PropTypes.node,
  };
  SFC.defaultProps = {
    bar: '',
    children: null,
  };
  ```

  - Use spread props sparingly.
  > Why? Otherwise you’re more likely to pass unnecessary props down to components. And for React v15.6.1 and older, you could [pass invalid HTML attributes to the DOM](https://reactjs.org/blog/2017/09/08/dom-attributes-in-react-16.html).

  Exceptions:

  - HOCs that proxy down props and hoist propTypes

  ```jsx
  function HOC(WrappedComponent) {
    return class Proxy extends React.Component {
      Proxy.propTypes = {
        text: PropTypes.string,
        isLoading: PropTypes.bool
      };

      render() {
        return <WrappedComponent {...this.props} />
      }
    }
  }
  ```

  - Spreading objects with known, explicit props. This can be particularly useful when testing React components with Mocha’s beforeEach construct.

  ```jsx
  export default function Foo {
    const props = {
      text: '',
      isPublished: false
    }

    return (<div {...props} />);
  }
  ```
  
  - Destruct your `props`

    ### More than 2 props from an object been used in the same place should be destructed

  Notes for use:
  Filter out unnecessary props when possible.

  ```jsx
  // bad
  render() {
    const { irrelevantProp, ...relevantProps } = this.props;
    return <WrappedComponent {...this.props} />
  }

  // good
  render() {
    const { irrelevantProp, ...relevantProps } = this.props;
    return <WrappedComponent {...relevantProps} />
  }
  ```



