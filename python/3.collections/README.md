## 📚 Collections
Choose your collection based on mutability and uniqueness needs.

- Lists: Ordered, mutable.
- Tuples: ordered, immutable
- Sets: unique, unordered
- Dicts: Key-value pairs

Mental Model: Choose based on mutability and uniqueness needs.

📊 Quick Comparison: Dict vs List vs Tuple vs Sets

| Feature | Dict | List | Tuple |Set|
| :--- | :--- | :--- |:--- |:--- |
| Structure | Key–Value pairs | Ordered elements |Ordered immutable elements|Unordered unique elements|
| Mutability | Mutable | Mutable |Immutable |Mutable|
| Indexing|By key|By index|By index|❌ Not supported|
|Duplicates|Keys unique, values can repeat|✅Allowed|✅Allowed|❌ Not allowed|
|Hashable|Keys must be immutable|❌Not supported|✅Allowed|❌Not supported|
|Use Case|Fast lookups, mappings|Dynamic collections|Fixed collections|Unique collections|
