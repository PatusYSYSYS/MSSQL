# 📊 Analiza sprzedaży miesięcznej

To repozytorium zawiera zapytanie SQL służące do analizy sprzedaży na poziomie miesięcznym na podstawie danych z tabeli `gold.fact_sales`.

## 🧠 Cel zapytania

Celem zapytania jest uzyskanie miesięcznego podsumowania sprzedaży z uwzględnieniem:

- Łącznej wartości sprzedaży
- Liczby unikalnych klientów
- Łącznej liczby sprzedanych sztuk

## 🗃️ Tabela źródłowa: `gold.fact_sales`

**Opis kolumn użytych w zapytaniu:**

| Kolumna        | Typ        | Opis                                      |
|----------------|------------|-------------------------------------------|
| order_date     | DATE       | Data złożenia zamówienia                  |
| sales_amount   | DECIMAL    | Wartość pojedynczej transakcji sprzedaży  |
| quantity       | INT        | Ilość sprzedanych sztuk                   |
| customer_key   | INT        | Unikalny identyfikator klienta            |

## 🧾 Zapytanie SQL

```sql
SELECT
  MONTH(order_date) as order_month,
  SUM(sales_amount) as total_sales,
  COUNT(DISTINCT customer_key) as total_customers,
  SUM(quantity) as total_quantity
FROM gold.fact_sales
WHERE order_date IS NOT NULL
GROUP BY MONTH(order_date)
ORDER BY MONTH(order_date);
