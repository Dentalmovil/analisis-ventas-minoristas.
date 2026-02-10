python --version
"Commit".
pip install yfinance pandas openpyxl
import yfinance as yf
import pandas as pd
import matplotlib.pyplot as plt

# 1. Configuración
ticker = "BTC-USD"
periodo = "1mo" # Puedes cambiarlo a "1y" para un año

# 2. Descarga y resumen técnico
print(f"Obteniendo datos de {ticker}...")
datos = yf.download(ticker, period=periodo, interval="1d")

# Mostramos un resumen estadístico en la terminal
print("\n--- Resumen Estadístico ---")
print(datos['Close'].describe()) 

# 3. Creación del gráfico
plt.figure(figsize=(10, 5))
plt.plot(datos['Close'], color='orange', label='Precio de Cierre')
plt.title(f'Evolución del Precio de {ticker}')
plt.xlabel('Fecha')
plt.ylabel('Precio (USD)')
plt.legend()
plt.grid(True)

# Guardamos el gráfico como imagen
plt.savefig("grafico_bitcoin.png")
print("\n¡Gráfico guardado como 'grafico_bitcoin.png'!")

# 4. Guardar en Excel
datos.to_excel("analisis_bitcoin_detallado.xlsx")
