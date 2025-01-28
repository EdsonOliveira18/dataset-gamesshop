# Scripts para Análise de Vendas
```python
import pandas as pd
```
# Carregar os dados
```python
file_path = 'Meganium_Sales_data.xlsx'
sales_data = pd.read_excel(file_path, sheet_name='consolidate')
```

# Análise de Vendas por País

```python
def analyze_sales_by_country(data):
    sales_by_country = data.groupby('delivery_country')['total_price'].sum().sort_values(ascending=False)
    return sales_by_country
```
# Identificar Produto mais Vendido

```python
    def identify_top_selling_product(data):
        product_sales = data.groupby('product_sold')['quantity'].sum(). sort_values(ascending=False)
        top_product = product_sales.idxmax()
      return top_product, product_sales[top_product]
```
# Geração de Relatórios

```python
def generate_report(data):
    # País com maior volume de vendas
    top_country_sales = analyze_sales_by_country(data)
    top_country = top_country_sales.idxmax()
    top_country_value = top_country_sales.max()

    # Produto mais vendido
    top_product, top_quantity = identify_top_selling_product(data)

    return {
        "top_country": top_country,
        "top_country_sales": top_country_value,
        "top_product": top_product,
        "top_quantity": top_quantity
    }
```
# Execução do Script
```python
if __name__ == "__main__":
    report = generate_report(sales_data)
    print("País com maior volume de vendas:", report["top_country"])
    print("Valor total de vendas no país:", report["top_country_sales"])
    print("Produto mais vendido:", report["top_product"])
    print("Quantidade vendida do produto mais vendido:", report["top_quantity"])
 ```