# Atomic Design
Atomic design is a methodology for designing and building user interfaces in a systematic and modular way. It involves breaking down the UI components into smaller, reusable building blocks called atoms, molecules, 
organisms, templates, and pages.

1. Atoms: Atoms are the basic building blocks of UI components. They represent the smallest and simplest elements, such as buttons, input fields, icons, or labels. These elements are typically self-contained and have minimal or no dependencies on other components.

2. Molecules: Molecules are groups of atoms that work together to form a more complex component. For example, a form input field combined with a label and a button can create a search bar molecule.

3. Organisms: Organisms are components that are composed of molecules and/or atoms. They represent more complex and complete sections of a UI. For instance, a navigation bar that consists of a logo, menu items, and a search bar can be considered an organism.

4. Templates: Templates provide the structure for a page or a specific section of a page. They define the placement and arrangement of organisms and other components, but they don't contain any specific content.

5. Pages: Pages are the final level of the atomic design hierarchy. They are instances where actual content is added to the templates. Pages represent the concrete implementation of the UI and are what users interact with.

<br>

```jsx
// Atoms
const Button = () => {
  return <button className="button">Click me</button>;
};

// Molecules
const SearchBar = () => {
  return (
    <div className="search-bar">
      <input type="text" className="search-input" placeholder="Search..." />
      <Button />
    </div>
  );
};

// Organisms
const NavigationBar = () => {
  return (
    <nav className="navigation-bar">
      <Logo />
      <MenuItems />
      <SearchBar />
    </nav>
  );
};

// Templates
const HomePageTemplate = () => {
  return (
    <div className="home-page">
      <NavigationBar />
      <Banner />
      <ContentSection />
      <Footer />
    </div>
  );
};

// Pages
const HomePage = () => {
  return (
    <HomePageTemplate />
  );
};

export default HomePage;
```

<br>

## Reference
https://medium.com/@janelle.wg/atomic-design-pattern-how-to-structure-your-react-application-2bb4d9ca5f97
