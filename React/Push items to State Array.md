In react in order to push items to an array we need to use the spreak syntax to let the state know that we want the current items in the array then we can push the newest item into the array.

```javascript
import {useState} from 'react';

export default function App() {
  const [names, setNames] = useState(['Alice', 'Bob']);

  const handleClick = () => {
    // 👇️ push to end of the state array
    setNames(current => [...current, 'Carl']);

    // 👇️ spread an array into the state array
    // setNames(current => [...current, ...['Carl', 'Delilah']]);

    // 👇️ push to the beginning of the state array
    // setNames(current => ['Zoey', ...current]);
  };

  return (
    <div>
      <div>
        <button onClick={handleClick}>
          Push to state array
        </button>
      </div>

      {names.map((element, index) => {
        return (
          <div key={index}>
            <h2>{element}</h2>
          </div>
        );
      })}
    </div>
  );
}

```