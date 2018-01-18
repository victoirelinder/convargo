# CONVARGO

> javascript workshop based on french startup https://www.convargo.com

![convargo](./convargo.png)

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Introduction](#introduction)
- [Objectives](#objectives)
- [Just tell me what to do](#just-tell-me-what-to-do)
  - [Don't forget:](#dont-forget)
- [Steps to to](#steps-to-to)
  - [Step 1 - Euro-Volume](#step-1---euro-volume)
    - [Shipping prices](#shipping-prices)
    - [Just tell me what to do](#just-tell-me-what-to-do-1)
  - [Step 2 - Send more, pay less](#step-2---send-more-pay-less)
    - [Decreasing pricing for high volumes](#decreasing-pricing-for-high-volumes)
    - [New price rules](#new-price-rules)
    - [Just tell me what to do](#just-tell-me-what-to-do-2)
  - [Step 3 - Give me all your money](#step-3---give-me-all-your-money)
    - [Commission](#commission)
    - [Just tell me what to do](#just-tell-me-what-to-do-3)
  - [Step 4 - The famous deductible](#step-4---the-famous-deductible)
    - [The deductible](#the-deductible)
    - [Just tell me what to do](#just-tell-me-what-to-do-4)
  - [Step 5 - Pay the actors](#step-5---pay-the-actors)
    - [The actors](#the-actors)
    - [Just tell me what to do](#just-tell-me-what-to-do-5)
- [Source and inspiration](#source-and-inspiration)
- [Licence](#licence)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Introduction

[Convargo](https://www.convargo.com/) wants to revolutionise the freight industry, by connecting shippers with truckers in real time via a web application.

The Goods freight transport sector is a key sector of the Europe (even worldwilde) economy:

* 300 billion euros in Europe
* 43 billion euros in France
* highly fragmented with more than 40,000 road transport companies in France
* under efficient: ⅓ trucks drive empty on Fance roads!

The [Convargo](https://www.youtube.com/watch?v=7hrDZluvtXo) platform allows shippers to:

* access directy to a wide range of road transport companies with available loading capacity
* compute and display the transport price calculated according to the best opportunities on the market at a time T
* track in real-time the goods delivery
* access to proof of transport and dematerialized invoices

## Objectives

We focus on this platform feature: `compute and display the transport price calculated according to the best opportunities on the market at a time T`.

The workshop goals are to

1. compute the shipping price for the `shippers`
2. compute the profit of the road transport company, the `truckers`
3. compute the profit of `convargo`

## Just tell me what to do

1. Fork the project via `github`
1. Clone your forked repository project `https://github.com/YOUR_USERNAME/convargo`

```sh
❯ cd /path/to/workspace
❯ git clone git@github.com:YOUR_USERNAME/convargo.git
```

1. Open the entry point[/public/index.html](./public/index.html) in your browser (that loads the `index.js` file)

```sh
# macos cli
❯ open public/index.html
# linux cli
❯ xdg-open public/index.html
# or by double-clicking in your browser files
```

1. Check the ouput in your browser console (Use `Ctrl + Shift + J` or `Cmd + Opt + J` to focus to your console devtools )
1. Solve each steps inside [./public/index.js](./public/index.js) file with JavaScript
1. Once a step is solved, commit your modification:

```sh
❯ cd /path/to/workspace/convargo
❯ git add -A && git commit -m "feat(price): decrease pricing for higher volume"
```

([why following a commit message convention?](https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#commits))

1. 5 steps, so ideally 5 commits
1. Don't forget to push before the end of the workshop

```sh
❯ git push origin master
```

**Note**: if you catch an error about authentication, [add your ssh to your github profile](https://help.github.com/articles/connecting-to-github-with-ssh/).

1. Check that your codebase works by checking the console output
1. If you need some helps on git commands, read [git - the simple guide](http://rogerdudler.github.io/git-guide/)

### Don't forget:

* DRY - Don't repeat yourself
* DOT - Do One Thing
* KISS - Keep It Simple Stupid
* LIM - Less Is More
* English only: codebase, variables, comments...

**Focus only on coding, forgot the browser display (next workshop!).**

**Use `console.log` to display results (for the moment)**

## Steps to do

### Step 1 - Euro-Volume

#### Shipping prices

The shipper books the trucker for an itinerary and volume.

The shipping price is the sum of the distance component and the volume component with

* **distance component**: the number of kilometers multiplied by the trucker price per km
* **volume component**: the used volume multiplied by the trucker price per m3

```
shipping price = distance + volume
```

#### Just tell me what to do

Write JS code that generates the shpping price for each `shipper` from `index.js` file:

```js
//example output from console.log
[
  {
    "id": "bba9500c-fd9e-453f-abf1-4cd8f52af377",
    ...
    "price": ?
  },
  {
    "id": "65203b0a-a864-4dea-81e2-e389515752a8",
    ...
    "price": ?
  },
  {
    "id": "165d65ec-5e3f-488e-b371-d56ee100aa58",
    ...
    "price": ?
  }
]
```

### Step 2 - Send more, pay less

#### Decreasing pricing for high volumes

To be as competitive as possible, convargo decide to have a decreasing pricing for high volumes.

#### New price rules

**price per m3**

* decreases by **10% after 5 m3**
* decreases by **30% after 10 m3**
* decreases by **50% after 25 m3**

#### Just tell me what to do

Adapt the shipping price computation to take these new rules into account.

```js
//example output from console.log
[
  {
    "id": "bba9500c-fd9e-453f-abf1-4cd8f52af377",
    ...
    "price": ?
  },
  {
    "id": "65203b0a-a864-4dea-81e2-e389515752a8",
    ...
    "price": ?
  },
  {
    "id": "165d65ec-5e3f-488e-b371-d56ee100aa58",
    ...
    "price": ?
  }
]
```

### Step 3 - Give me all your money

Now, it's time to pay the truckers

Convargo take a 30% commission on the shipping price to cover their costs.

#### Commission

The commission is split like this:

* **insurance**: half of commission
* **the Treasury**: 1€ by 500km range
* **convargo**: the rest

#### Just tell me what to do

Compute the amount that belongs to the insurance, to the assistance and to convargo.

```js
//example output from console.log
[
  {
    "id": "bba9500c-fd9e-453f-abf1-4cd8f52af377",
    ...
    "commission": {
      "insurance": ?,
      "treasury": ?
      "convargo": ?
    }
  },
  ...
]
```

### Step 4 - The famous deductible

In case of an accident/theft, convargo applies a 1000€ deductible.

The shipper can reduce the deductible amount from 1000€ to 200€ with a `deductible option` for a few more euros per volume.

#### The deductible

The driver is charged an additional 1€/m3 when he chooses the `deductible reduction` option.

**The additional charge goes to convargo, not to the trucker.**

#### Just tell me what to do

Compute the new amount price if the shipper subscribed to `deductible option`.

```js
//example output from console.log
[
  {
    "id": "bba9500c-fd9e-453f-abf1-4cd8f52af377",
    'options': {
      'deductibleReduction': true
    },
    ...
    "price": ?
  },
  ...
]
```

### Step 5 - Pay the actors

#### The actors

It's time to debit/credit each actor!

- **the shipper** must pay the **shipping price** and the **(optional) deductible reduction**
- **the trucker** receives the **shipping price** minus the **commission**
- **the insurance** receives its part of the **commission**
- **the Treasury** receives its part of the tax **commission**
- **convargo receives** its part of the **commission**, plus the **deductible reduction**

#### Just tell me what to do

* Compute the debit for the `shipper`
* Compute the credit of the car `trucker`, `insurance`, and `convargo`.

```js
//example output from console.log
[
  {
    "deliveryId": "bba9500c-fd9e-453f-abf1-4cd8f52af377",
    "payment": [
      {
        "who": "shipper",
        "type": "debit",
        "amount": ?
      },
      {
        "who": "owner",
        "type": "credit",
        "amount": ?
      },
      {
        "who": "insurance",
        "type": "credit",
        "amount": ?
      },
      {
        "who": "treasury",
        "type": "credit",
        "amount": ?
      },
      {
        "who": "convargo",
        "type": "credit",
        "amount": ?
      }
    ]
  },
  ...
]
```

## Source and inspiration

* [Convargo](https://www.convargo.com/)
* [Drivy Challenges](https://github.com/drivy/jobs)

## Licence

[Uncopyrighted](http://zenhabits.net/uncopyright/)
