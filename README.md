# Cayan Delphi Components

Delphi Component Library for Payment Processing using [Cayan's Payment Gateway Solutions](http://www.cayan.com), enabling retail software to collect various forms of payment, including chip cards (EMV), phone taps (Proximity), and more. 

## Disclaimer

This library was written by Jerry Dodge, and not by any direct member of Cayan. No guarantees are made towards this code, and is available on an as-is / what-is basis. Neither I or Cayan are responsible for any problems which may arise as a result of using this code. You are responsible to ensure this code base suites your application's needs, and abides by the PCI compliance laws set with implementing Genius solutions. 

## Disclaimer

While this library is free and open-source, you are still responsible to acquire certification with Cayan to be allowed to work with their solutions. This library only wraps Cayan's APIs, and you must treat the integration the same as if you wrote this library. Certification works on a per-application basis, so even one certification is not enough to use this library indefinitely. The end goal is to become [PCI Compliant](http://www.onlinetech.com/resources/references/what-is-pci-compliance) with the Genius solutions. 

Please visit the [Cayan Developer's Page](https://cayan.com/developers) for more information.

## Super Object

This library uses its own copy of X-SuperObject. Since there were modifications in those units to be able to work as needed, it was necessary to include them in this repo. However, it must be noted that the units `Cayan.XSuperObject` and `Cayan.XSuperJSON` were not actually written with the rest of this library.

## Delphi Support

This library was written for Delphi 10 Seattle, and recently tested in Delphi 10.1 Berlin. While it should work in most modern Delphi versions, it has not been tested, and there is no guarantee that it will be compatible. It is cross-platform compatible, but not thoroughly tested on any platform other than Windows (32bit and 64bit). It does not depend on VCL or Firemonkey. Past versions of this library have been successfully deployed to MacOS, iOS, and Android, but have gone through extensive modifications since then. All current testing is only on Windows.

The test applications use a combination of VCL and Firemonkey. The Emulator and the POS applications are both based on the Firemonkey framework, while the stand-alone test application is on the VCL framework. 

## Delphi Packages

There are two packages included: A Run-Time package, and a Design-Time package. Each must be installed into the Delphi IDE the same as any standard package.

1. Open the Run-Time Package `CayanComponentsDX10.dpk` and `Build` the project.
2. Open the Design-Time Package `dclCayanComponentsDX10.dpk` and `Build` the project.
3. While still in the Design-Time Package, `Install` the project.
4. You shall be notified that the components were successfully installed.
5. Open `Tools` > `Options`, then navigate to `Environment Options` > `Delphi Options` > `Library`, choose the appropriate `Selected Platform`, then click on the `[...]` button to the right of `Library Path`. 
  1. Enter the directory of the `.\Source` dir and press `Add`. 
  2. Enter the directory of the `.\Libraries\X-SuperObject` dir and press `Add`.
  3. Press `OK`, and `OK`.

## Component Pallette

The following components are installed into the Delphi IDE Tool Pallette under the `Cayan` tab:

### `TCayan`

Represents a single connection to Cayan's systems, and is not related to any particular service or solution. It only carries the API credentials, company, user, and station information. It is further used by other components to be able to share the same connection using this `TCayan` component.

### `TCayanGenius`

Represents a single connection to one of Cayan's Genius CED payment terminals. Provides the ability to perform various general tasks, but most importantly, attaching other components which control various tasks.

### `TCayanGeniusTransaction`

Represents a single transaction being made using one of Cayan's Genius CED payment terminals. Provides details for a single payment transaction.

### `TCayanGeniusLineItems`

Allows you to utilize Line Item Display on the device. Attaches to a `TCayanGeniusTransaction` component. 

### `TCayanGeniusAgreement`

Allows you to send a command to the Genius device requesting the consumer to either Accept or Decline an agreement, while displaying a scrollable text area where an agreement is displayed. Attaches to a `TCayanGeniusTransaction` component. 

### `TCayanGeniusEmulator`

Allows you to serve a virtual emulator, mimicing a real Genius CED device. This component is primarily used in the Genius CED Emulator application. This project has been put on hold until the real CED payment terminal can be completely implemented. 

### `TCayanPOSServer`

Represents a web server which provides access from a `TCayanPOS` component to its underlying back-end database. 

### `TCayanPOS`

Represents a single instance of a Point-of-Sale application. Used for connection from the POS application to its corresponding server. 

## POS Application

There is a test application provided with this repo, which demonstrates actual usage of the Genius solution by a Point-of-Sale application. It is developed for the purpose of demonstrating actual usage of the Genius solutions. 

![POS](./Readme/POS_SS.png?raw=true)

## Genius CED Emulator

Included is an emulator application which mimics a Genius device. This emulator can be used in place of a real device, and allows you to test your own integration with Genius without actually needing a device of your own. While the device is as close as possible to the real thing, it is not capable of actually processing real payments. 

**NOTE** This emulator is far from complete, and should not be trusted at this time. 

![Emulator](./Readme/EmulatorMX915.png?raw=true)

## Instructions

Complete instructions are included in this repo under the `Readme` folder.

1. [Getting Started](./Readme/Chapter%201%20-%20Getting%20Started.md)
2. [MerchantWare Transactions](./Readme/Chapter%202%20-%20MerchantWare%20Transactions.md)
3. [Genius](./Readme/Chapter%203%20-%20Genius.md)
4. [Genius Transactions](./Readme/Chapter%204%20-%20Genius%20Transactions.md)

