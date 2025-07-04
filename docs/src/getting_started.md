# Getting started
This package provides multiple algorithms for Blind Source Separation. 
At this time the user can choose between JADE, Shibbs and Picard. 

## How to use the datatype SensorData
Key to using the package is the SensorData datatype. The user can either create a SensorData instance by loading it from disk using the read_dataset() function, or he can construct his own by provididing an array of timestamps of length N and a corresponding matrix of size NxM, where M is the amount of sensors in the dataset.
When the user has created a SensorData instance, he can pass it to the whitening function, plot it or perform the Blind Source separation using the perform_separation function.

## Code Example 
Load a dataset from disk

    x = read_dataset("data/foetal_ecg.dat")

Perform whitening on the dataset

    x = whiten_dataset(x)

Plot dataset

    plot_dataset(x)

Prepare JADE algorithm

    algo = Jade(size(x.data, 2))

Prepare Shibbs algorithm

    algo = Shibbs(size(x.data, 2))

Prepare Picard algorithm

    algo = Picard()

Run source separation

    x = perform_separation(x, algo)

Plot again

    plot_dataset(x)

### Complete example:

This example plots the original whitened data, as well as the results of Jade and Shibbs algorithm.

    x = read_dataset("data/foetal_ecg.dat")
    x = whiten_dataset(x)
    plot_dataset(x)

    algo = Jade(size(x.data, 2))
    y = perform_separation(x, algo)
    plot_dataset(y)

    algo = Shibbs(size(x.data, 2))
    z = perform_separation(x, algo)
    plot_dataset(z)