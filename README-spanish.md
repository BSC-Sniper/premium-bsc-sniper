### BSC Sniper

Siempre que sale un proyecto nuevo en la red BSC nos frustamos porque no podemos comprar al momento de la salida. 

BSC Sniper es una herramienta que te ayudará a comprar token de proyectos en la red BSC que sean listados en PancakeSwap o ApeSwap mucho más rápido que cualquiera. Es fácil de usar, y corre local en tu máquina. No necesitas enviarme nada, solo una pequeña donación si esto funciona para ti :D

<H2>Prerequisitos</H2>

 - Tu billetera de la BSC (Binance Smart Chain). Tu metamask por ejemplo. 
 - Un equipo Windows x64
 - Internet, obviamente para conectarte a la red BSC.

<H2>Empezemos</H2>

1. Clona (Descarga) este repositorio <a href="https://github.com/BSC-Sniper/free-bsc-sniper">aqui</a>.
2. Descargaras un archivo .zip. Extráelo en tu Escritorio o cualquier carpeta que quieras.
3. Una vez extraido el .zip, vas a ver una carpeta que se llama _"free-bsc-sniper"_ y dentro de ella alrededor de 56 archivos (**NO ELIMINES NI CAMBIES NIGUN ARCHIVO**). Estos son los más importantes:
    - **config.json** ; el más importante. Este es el que contiene los datos para tus consultas y transacciones.
    - **abi.json** ; este es el de los contractos ABI. No necesitas cambiar nada aqui, a menos que necesites. Los ABI son los parametros que puedes leer/escribir en los contractos en la BSC. Si eres curioso y quieres aprender un poco más sobre esto: https://www.quicknode.com/guides/solidity/what-is-an-abi
    - **bscsniper.exe** ; el ejecutable, la magia.
4. Copia la ruta de la carpeta donde descomprimiste el .zip (ejemplo: C:\Users\user\free-bsc-sniper\bscsniper) y luego abre el terminal cmd (_Windows Search > cmd_) y ve a la carpeta que acabas de copiar usando el comando `cd` (cambiar directorio) > ejemplo: `cd C:\Users\user\free-bsc-sniper\bscsniper`
5. Ya estas listo para ejecutar. Puedes ejecutar `bscsniper.exe --help` y encontraras todas las opciones disponibles.

<H2>Archivo de Configuración (config.json)</H2>

Ubica y abre con un editor de texto el archivo **_config.json_** que está en la carpeta. Encontraras estos parametros:

```
{
  "pancakeFactory":"0xcA143Ce32Fe78f1f7019d7d551a6402fC5350c73",
  "pancakeRouter":"0x10ED43C718714eb63d5aA57B78B54704E256024E",
  "yourWallet":"YOUR_WALLET_HERE",
  "yourPrivateKey":"YOUR_PRIVATE_HERE",
  "BNB":"0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c",
  "BUSD":"0xe9e7cea3dedca5984780bafc599bd69add087d56"
}
```

Asegurate de cambiar `YOUR_WALLET_HERE` y `YOUR_PRIVATE_HERE` por tu informacion.

- **pancakeFactory**: Este es el contracto Factory de Pancakeswap. Con este contracto es que los proyectos en la BSC crean el par TOKEN/BNB o TOKEN/BUSD, y crean el Liquidity Pools (LP). Este es usado para validar si el token que quieres comprar ya tiene un par asignado, ya sea BNB o BUSD. No significa que aún tenga liquidez. No necesitas cambiar nada aquí, si quieres usar PancakeSwap. Esta información la puedes encontrar y validar directamente en la página de PancakeSwap (PancakeSwap Factory V2): https://docs.pancakeswap.finance/code/smart-contracts. 
- **pancakeRouter**: Este es el contracto que usa PancakeSwap para la compra/venta de los tokens, aún si los compras por su página, en realidad estas pasando por este contracto. No necesitas cambiar nada aquí, si quieres usar PancakeSwap. Esta información la puedes encontrar y validar directamente en la página de PancakeSwap (PancakeSwap Router V2): https://docs.pancakeswap.finance/code/smart-contracts.
- **yourWallet**: Tu dirección de Metamask o tu billetera. Esta es la billetera que vas a usar para comprar/vender los tokens. Obviamente necesitas tener BNB para pagar los fees.
- **yourPrivateKey**: Esta es tu llave privada (Private Key) de tu billetera y es usada para firmar las transacciones que hagas. Si no configuras esta llave, no podrás comprar/vender/aprobar ningun token.  Si no sabes como encontrarla, puedes ver este articulo: https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key. **ESTA NO ES TU FRASE SECRETA, NI TU SEMILLA. DE IGUAL MANERA NO LO COMPARTAS CON NADIE, NI TU LLAVE PRIVADA NI TU FRASE SECRETA. NO COMPARTAS ESTA INFORMACION CON NADIE. ES SOLO TUYA.**
- **BNB**: token WBNB. Es usado si quieres comprar/vender/aprobar un token con este pair (BNB). No necesitas cambiar nada aquí. Puedes validar la información en CMC: https://coinmarketcap.com/currencies/wbnb/
- **BUSD**: token BUSD. Es usado si quieres comprar/vender/aprobar un token con este pair (BUSD). No necesitas cambiar nada aquí. Puedes validar la información en CMC: https://coinmarketcap.com/currencies/busd/

**IMPORTANTE**: Si, lo sé.. Sé que el parametro de "yourPrivateKey" te asusta (a mi también me asustó al principio), pero lo necesitaras si quieres comprar un token más rápido que cualquiera.

Otra cosa, si el token que quieres comprar se está listando en ApeSwap, necesitarás cambiar los parámetros de "pancakeFactory" and "pancakeRouter". Pero SOLO CAMBIA LOS VALORES (contractos), NO CAMBIES LOS NOMBRES. No importa si el archivo dice "pancakeFactory" y el valor es el contracto de ApeSwap. NO CAMBIES EL NOMBRE, solo los contractos, o el script va a fallar.

La información de los contratos Router y Factory de ApeSwap la pueden encontrar directamente en su documentación: (ApeFactory and ApeRouter): https://apeswap.gitbook.io/apeswap-finance/smart-contracts

Por ejemplo, deberías cambiar _"0xcA143Ce32Fe78f1f7019d7d551a6402fC5350c73"_ a _"0x0841BD0B734E4F5853f0dD8d7Ea041c241fb0Da6"_.

<H2>Funciones</H2>

Ok. Que funciones tienes disponibles para usar:

 - Validar si ya existe un contrato LP para el par que deseas validar (por ejemplo, CAKE/BNB o CAKE/BUSD) (por defecto lo hace)
 - Validar si hay liquidez en el par. (por defecto lo hace)
 - Mostrar tu balance (opcional)
 - Mostrar el precio del token si quieres. Por ejemplo, si estas usando CAKE, el script te mostrara el precio de CAKE en USD. (opcional)
 - Validar si el token que estas queriendo comprar/vender ya esta aprobado en tu billetera. Si no esta aprobado, el script lo aprobará por ti. De igual manera, puedes validar tu mismo esta información en https://bscscan.com/tokenapprovalchecker colocando tu wallet. **NOTA**: Si anteriormente ya has aprobado tokens, sabrás que se paga un fee por esto, es insignificante pero para que lo tengas en cuenta (cerca de 0.12 USD). No te preocupes, el script te mostrara la transaccion. (Esto es opcional, y deberías hacerlo antes del listamiento para no perder tiempo, y si quieres vender el token rápido).
 - COMPRAR un token (si usas los parametros correctos). Lo sé, por eso estas aquí.
 - VENDER un token.
 - Configurar Slippage en tus ordenes de compra (solo COMPRAS).
 - Validar si el contracto tiene Protection contra bots (BPEnabled).

 NOTA: La aprobación de un token permite poder vender ese token que esta aprobado. Si ya antes has hecho swap de BNB y BUSD ya lo deberias tener aprobado, obviamente, pero los tokens nuevos debes aprobarlos antes de poder venderlos (cambiar CAKE por BNB, por ejemplo). Esto también lo puedes hacer en https://poocoin.app por ejemplo, sin embargo si el token no ha salido publicamente con liquidez, no te va a dejar hacerlo. Es mejor hacerlo directamente en la BSC, antes del lanzamiento.

 <H2>¿Cómo usas estas funciones?</H2>

 Fácil. Si seguiste correctamente el apartado  "Empezemos" y "Archivo de configuración" estas listo para iniciar.

 En tu linea de comando cmd (recuerda, debes estar en la carpeta donde descomprimiste los archivos), execute `bscsniper.exe --help` or `-h`. Ahí encontraras todas las opciones que mencioné antes:
```
  -h, --help            show this help message and exit
  --spend SPEND, -s SPEND
                        Spender Symbol BNB or BUSD
  --gas GAS, -g GAS     Gas
  --amount AMOUNT, -a AMOUNT
                        Amount to buy/sell
  --contract CONTRACT, -c CONTRACT
                        Contract of the Token
  --approval, -A        Check allowance
  --sell                Selling Process only BNB)
  --buy                 Buying Process (only BNB or BUSD)
  --balances, -b        Check your balances (optional)
  --price, -p           Check token price (optional)
  --slippage, -sp       Set the slippage in percentage (buy only) (optional)
  --bpEnabled, -bp      Check if Bot Protection exists (optional)
```
 Entonces, primero, los parametros **REQUERIDOS** son 1. el CONTRACTO (token que quieres comprar/vender) y 2. el pair que vas a gastar (BNB o BUSD).

 Estos son algunos ejemplo que puedes usar. Usaré como ejemplo CAKE y lo quiero comprar con BNB. Si:

 **Quieres ver si funciona la herramienta:**
```
 bscsniper.exe -c 0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82 -s BNB
```
 Así de fácil. Vas a obtener:

  - Si estas conectado o no a la red de BSC.
  - Si CAKE tiene un contracto LP con BNB. 
    - Si no (como es normal antes del listamiento), el script se quedara esperando que haya un contracto.
    - Si sí tiene un contrato LP con BNB, luego validará si tiene liquidez. 
        - Si no tiene liquidez If there is no liquidity (como es normal antes del listamiento, otra vez), el script se quedara esperando hasta que la liquidez se agregada (al menos 10.000 tokens por defecto, si hay menos liquidez de esa, el script seguirá esperando).

**Quieres ver tu balance:**
```
 bscsniper.exe -c 0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82 -s BNB -b
```
  - Veras todas la información de antes (liquidez, etc)...
  - ..y tu balance para ambos. En este caso, mostrará el balance que tienes para CAKE y para BNB.

**Quieres validar el precio del token (obviamente, esto solo funciona si el token tiene liquidez):**
```
 bscsniper.exe -c 0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82 -s BNB -p
```
  - Veras todas la información de antes (liquidez, etc)...
  - ..y luego verás el precio de CAKE en USD.

**Quieres validar si el token esta aprobado y/o aprobar el token:**
```
 bscsniper.exe -c 0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82 -s BNB -A
```
  - El script validará si ya el token ha sido aprobado. Si sí, te dirá "It's approved" y continua su curso normalmente (Veras todas la información de antes (liquidez, etc)...)
  - Si el token NO está aprobado, el script lo aprobará automáticamente por ti. Vas a poder ver el ID de la transacción en la bscscan.com. Recuerda que aprobar un token tiene un pequeño fee en la red de BSC (cerca de 0.12 USD) ...y luego, veras todas la información de antes (liquidez, etc).

**Quieres COMPRAR (obviamente, esto solo funciona si el token tiene liquidez):**
```
bscsniper.exe -c 0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82 -s BNB -g 5 -a 0.1 --buy
```
 - Como puedes ver, hay tres nuevos argumentos:
    - `-g` o `--gas` es para especificar el gas que quieres gastar en tu transacción in GWEI. Esto es exactamente lo mismo como cuando lo cambias directamente en tu Metamask y quieres editar tu gas, pero este es mucho más rápido y fácil (sin clics en Metamask, edit, edit, confirm). Recuerda que si quieres comprar tokens más rápido, necesitas colocar un gas alto. Puede ser 10 o 50, como quieras.
    - `-a` o `--amount` es la cantidad que quieres gastar. Por ejemplo si elegiste gastar en BNB, esta sera la cantidad en BNB que quieres gastar (solo la cantidad, sin el simbolo). Por ejemplo si colocas `-s BNB -a 0.1` vas a gastar **0.1 BNB**, si colocas `-s BUSD -a 100` vas a gastar **100 BUSD**. 
    - `--buy` es el indicador de que quieres COMPRAR. Si pones este flag, le estas diciendo al script que quieres comprar y va a intentar ejecutar la compra en la BSC. Vas a poder ver el ID de la transacción en la bscscan.com
 - Veras todas la información de antes (liquidez, etc)...
 - Luego, vas a poder ver el ID de la transacción en la BSC Scan (el enlace) y el script esperará y mostrará el estado de la transacción, si falló o fue exitosa. 

**Quieres VENDER (obviamente, esto solo funciona si el token tiene liquidez):**
```
bscsniper.exe -c 0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82 -s BNB -g 5 -a 10 --sell
```
 - Es el mismo proceso de comprar pero en vez de usar `--buy`, debes usar **`--sell`**, y tienes que cambiar  `-a` por la cantidad de tokens que quieras vender por BNB. Por ejemplo, si quieres vender " 10 CAKE", debes colocar `-a 10` y vas a cambiar 10 CAKE por BNB, al precio del momento. **Importante: La caracteristica de vender solo funciona para BNB, no para BUSD, por ahora**

## PROBLEMAS
Hay algunas razones por las cuales tu transaccion puede fallar:
 - La configuracion del gas es muy pequeño.  Te lo dije arriba!!!
 - No tienes suficiente balance para pagar el fee + la compra. Recuerda que debes tener BNB para pagar fees, incluso si estas usando BUSD para comprar un token.
