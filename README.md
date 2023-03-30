# Taller: De notebook a modelo en producción

## Resumen

1. Crear una biblioteca Python con el código reutilizable correspondiente al proyecto
   y probar que funciona desde un intérprete de Python
2. Crear una aplicación web usando FastAPI que haga uso de ese código
   y probar que funciona desde Gitpod
3. Desplegar la aplicación web en Railway

## Referencias

- https://github.com/astrojuanlu/ie-mbd-advanced-python/

## Enlaces

- https://fastapi.tiangolo.com/
- https://www.gitpod.io/
- https://voila.readthedocs.io/
- https://shiny.rstudio.com/py/
- https://railway.app/?referralCode=VO2J82 (afiliado)

## Instrucciones


local machine (linux)

```
python -m venv .venv
source .venv/bin/activate
pip install -U pip pip-tools
pip-compile
pip install -r requirements.txt
pip install flit
mkdir library && cd library
flit init
pip install black
pip install pandas
pip install joblib
pip install -U scikit-learn
pip install matplotlib
pip install seaborn
uvicorn app:app --reload
```

local machine (windows)

```
editar el archivo "library/bikesmodel/__init__.py" cambiando la ruta de joblib, por ejemplo en mi caso puse:

    joblib.dump(reg, r"\tmp\model.joblib")    
    #joblib.dump(reg, r"C:\Users\pbioscauser\AI\model.job")

def predict(dteday, hr, weathersit, temp, atemp, hum, windspeed) -> int:
    model = joblib.load( r"\tmp\model.joblib")
    #model = joblib.load(r"C:\Users\pbiosca\AI\model.job")

python -m venv .venv
cd .venv/Scripts
./activate
pip install -U pip pip-tools
cd..
cd..
pip-compile
pip install -r requirements.txt
pip install flit
flit init
pip install black
copy app.py to .venv/Scripts 
pip install pandas
pip install joblib
pip install -U scikit-learn
pip install matplotlib
pip install seaborn
uvicorn app:app --reload
```


Remote machine (Gitpod)

```
pip install pandas
pip install joblib
pip install -U scikit-learn
pip install matplotlib
pip install seaborn
uvicorn app:app --reload
```