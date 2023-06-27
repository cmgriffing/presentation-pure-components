## Example

## Non-pure

```ts
function MyPageComponent() {
  const [items, setItems] = useState<string[]>([]);

  useEffect(() => {
    async function fetchItems() {
      const response = await fetch("foo.json");
      const fetchedItems = await response.json();
      setItems(fetchedItems);
    }
    fetchItems();
  }, []);

  return (
    <div>
      {items.map((item) => (
        <div>{item}</div>
      ))}
    </div>
  );
}
```

## Refactored

```ts
function MyPageComponent() {
  const [items, setItems] = useState<string[]>([]);

  useEffect(() => {
    async function fetchItems() {
      const response = await fetch("foo.json");
      const fetchedItems = await response.json();
      setItems(fetchedItems);
    }
    fetchItems();
  }, []);

  return <ItemsList items={items} />;
}

function ItemsList({ items }: { items: string[] }) {
  return (
    <div>
      {items.map((item) => (
        <div>{item}</div>
      ))}
    </div>
  );
}
```

## Why?

Testing via Jest etc.

Jest is an order of magnitude faster than Cypress.

```tsx
<ItemsList items={[]} />

<ItemsList items={["foo"]} />

<ItemsList items={["foo", "bar"]} />
```

---
