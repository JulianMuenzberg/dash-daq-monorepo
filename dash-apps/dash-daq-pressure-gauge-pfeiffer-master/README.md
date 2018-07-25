# dash-daq-pressure-gauge-pfeiffer

## Introduction
`dash-daq-pressure-gauge-pfeiffer` is a repository created to interface pfeiffer pressure gauges controllers with dash DAQ.

1. Pfeiffer TPG256A multi-gauge controller
[Demo app on Heroku](https://dash-daq-pressure-gauge-pv.herokuapp.com/), and dashdaq.io [blog post](https://www.dashdaq.io/read-pfeiffer-vacuum-gauge-pressure-in-python). 

### [Technique/field associated with the instrument]
Low pressure gauges (1 atmosphere and below) are used in vacuum environnements. 

### dash-daq
[Dash DAQ](http://dash-daq.netlify.com/#about) is a data acquisition and control package built on top of Plotly's [Dash](https://plot.ly/products/dash/).


## Requirements
It is advisable	to create a separate virtual environment running Python 3 for the app and install all of the required packages there. To do so, run (any version of Python 3 will work):

```
python3 -m virtualenv [your environment name]
```
```
source activate [your environment name]
```

To install all of the required packages to this environment, simply run:

```
pip install -r requirements.txt
```

and all of the required `pip` packages, will be installed, and the app will be able to run.


## How to use the app

To control your gauge controller, you need to input your COM port number in the `app.py` file and set the mock attribute to `False`

```
pressure_gauge = TPG256A(
  instr_port_name=[your instrument's com port],
  mock=False,
  gauge_dict={'P1': 'mbar', 'P4': 'mbar'}
)
```

Your gauges in `gauge_dict` should be named after the convention `P<input number of the gauge>` for pressure to be read by the gauge controller. 

You can then run the app :

```
$ python app.py
```

if you don't have the instrument connected to your computer but would still like to test the app you can run

```
$ python app_mock.py
```

## Resources
Manual of the Pfeiffer [TPG256A](https://www.idealvac.com/files/ManualsII/Pfeiffer_MultiGauge256A_OpInstructions.pdf)
