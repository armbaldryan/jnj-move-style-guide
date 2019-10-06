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

## Basic Rules

  - Follow DRY (Don’t repeat yourself), KISS (Keep it small and simple), DIE (Duplication Is Evil), YAGNI (You Ain’t Gonna Need It), SOLID principles
  - 
  
  
## Naming

  - **Extensions**: Use `.tsx` extension for React components with typescript.
  - **Filename**: Use PascalCase for filenames. E.g., `ReservationCard.tsx`.
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

