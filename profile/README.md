![wordmark-Antelope-fixed](https://github.com/user-attachments/assets/331e76e2-c63d-4456-aeab-24afaeecfcfc)

# Antelope LCA
A framework for distributed computation of LCA results.

## Quick Links

 * [Antelope Interface](https://antelopelca.github.io/antelope) Documentation
 * [Antelope Core Implementation](https://antelopelca.github.io/core) Documentation
 * [User Guides and Demos](https://github.com/AntelopeLCA/user), including support (via issues and [gitter])

## Quick Install

The minimal installation includes only a few upstream dependencies so you can perform LCA without downloading very much (no `scipy`, `pandas`, or `matplotlib`, for instance).  

```shell
$ python -m venv my_new_env
$ source my_new_env/bin/activate
(my_new_env) $ pip install antelope-core
(my_new_env) $ ipython
```
```python
>>> from antelope_core import LcCatalog
>>> cat = LcCatalog()
>>> cat.blackbook_guest('https://sc.vault.lc')
>>> 
```
This is sufficient for you to obtain data from a remote server and perform LCI/A operations and benchmarking. However, for modeling, you 
will need `antelope-foreground`; for performing LCI and partial ordering you will need `antelope-background` which adds back in `scipy`,
(you may also want `lxml` for loading Ecospold or ILCD files); and for charts and reporting, you will need `antelope-reports` (which brings back
`pandas` and `matplotlib`, among others).

For more information on different installed configurations, check out [TBD]

## Making big problems smaller

Antelope is based on the concept that different kinds of information in LCA are needed for different purposes, and that storing and managing that information doesn't need to happen in 
one place or all at once.  Antelope describes LCA computation in terms of different **interfaces**:

| Interface | Type of Information | Example | Values | Users may update | 
|-----------|---------------------|-------- |--------|-------|
| basic     | Documentary / Metadata / LCIA Indicators | EPDs | Indicator Values | Docs + Metadata |
| exchange  | Activity Descriptions and direct requirements | Unit Process Dataset | Reference Exchange Values | Exchanges and Exchange values | 
| background| Economic / market models | LCI dataset | LCI data values | allocation and linking|
| quantity  | Flow properties and characterization | LCIA Methodology | Characterization Factors| NA|
| foreground| Product System Models, Relationships, Scenarios| Suppliers and customers | Dynamic exchange values | observations|

These interfaces can be implemented by different services, independently of one another.  Moreover, data owners can control
which parts of these interfaces can be accessed by whom.


## Privacy and Publishing

One key challenge Antelope was designed to address is the lack of "in-between" options for privacy.  The most promising options for sharing 
LCI data at present involve contributing the dataset in its entirety to a third-party database, like ecoinvent or the Federal LCA Commons. 
When a study author does this, they lose control over their content.  In the Antelope framework, a data owner can publish a study themselves, 
and control what aspects of the above interfaces different users may access.  This is achieved by publishing a link to the study on an 
authentication server, and then issuing grants to individual users that permit them various shades of access.

<img src="https://github.com/user-attachments/assets/e424c325-e32f-4a1a-941d-076e9db0be35" width=400 />


## The shared model is the source of meaning

Use Antelope software to host a [data-free model](data-free-model.pdf) to describe your study and system boundary, and disclose limited
inventory and impact information to selected users while concealing it from others.  The use of a shared model can turbocharge efforts 
at multi-party **verification** of studies and analytic systems.

## Open source

All the core tools for `antelope.py` are open source and available on the [Python Package Index](https://pypi.org/). 
A
