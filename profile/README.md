![wordmark-Antelope-fixed](https://github.com/user-attachments/assets/331e76e2-c63d-4456-aeab-24afaeecfcfc)

# Antelope LCA
A framework for distributed computation of LCA results.

## Separation of Concerns

Antelope is based on the concept that different kinds of information in LCA are needed for different purposes, and that storing and managing that information doesn't need to happen in 
one place or all at once.  Antelope describes LCA computation in terms of different **interfaces**:

| Interface | Type of Information | Example | Values | Users may update | 
|-----------|---------------------|-------- |--------|-------|
| basic     | Documentary / Metadata / LCIA Indicators | EPDs | Indicator Values | Docs + Metadata |
| exchange  | Activity Descriptions and direct requirements | Unit Process Dataset | Reference Exchange Values | Exchanges and Exchange values | 
| background| Economic / market models | LCI dataset | LCI data values | allocation and linking|
| quantity  | Flow properties and characterization | LCIA Methodology | Characterization Factors| NA|
| foreground| Product System Models, Relationships, Scenarios| Suppliers and customers | Dynamic exchange values | observations|


## Privacy and Publishing

One key challenge Antelope was designed to address is the 



Simplify the data challenges of LCA by breaking big problems into small ones
 - **xdb** - exchange database - stores background LCI from published data sources
 - **qdb** - quantity database - flow characteristics, hazard traits, properties, LCIA, and regionalization
 - **oryx** - model runner - share product models and computation results

## The shared model is the source of meaning

Use Antelope software to host a [data-free model](data-free-model.pdf) to describe your study and system boundary

## Designed for EPD

Construct *consistent* and *comparable* EPDs using shared models.

## Open source

Use [antelope.py](https://github.com/AntelopeLCA/antelope) to compute with free data today!
