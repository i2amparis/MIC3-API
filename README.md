# MIC3-API

Common OpenAPI contract for model adapters participating in the MIC3 framework.

The API defines how workflow tools can interact with different models through a
shared interface while each model adapter handles the model-specific details,
such as native input files, configuration files, simulation commands, and output
formats.

For more information on MIC3 visit: [https://www.transience.eu/mic3-platform](https://www.transience.eu/mic3-platform)

## API scope

This first version covers the basic adapter operations:

- Retrieve model and adapter information.
- Create and retrieve model input files.
- Retrieve model output files.
- Retrieve and update model configuration files.
- Start, monitor, log, and cancel model simulations.

The OpenAPI specification is in [`openapi.yaml`](openapi.yaml).

## Data exchange formats

Input files use IAMC long-format CSV with the required columns:

```text
model, scenario, region, variable, unit, year, value
FORECAST, Baseline, Spain, Price|Final Energy|Industry|Plastics|Electricity, USD_2010/GJ, 0.09 
```

Configuration updates use a generic two-column CSV:

```text
parameter, value
end_year, 2050
```

Each model adapter maps these generic configuration and input parameters to the model's native files.

## Latest files

List endpoints support retrieving the latest available file with:

```text
GET /inputs?limit=1&sort=-created_at
GET /outputs?limit=1&sort=-created_at
```

## Interactive documentation (Swagger UI)

Interactive documentation using Swagger UI is available at [https://api.transience.eu](https://api.transience.eu). The documentation page visualises directly the [`openapi.yaml`](openapi.yaml) and is kept up to date with its changes.

For local preview, serve the repository root and open `/docs/`:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000/docs/
```

## License

This project is licensed under the Apache License 2.0. See [`LICENSE`](LICENSE).

## Funding

The TRANSIENCE project has received funding from the European Union’s HORIZON EUROPE Research and Innovation Programme under grant agreement No [101137606](https://doi.org/10.3030/101137606). Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Health and Digital Executive Agency (HaDEA). Neither the European Union nor the granting authority can be held responsible for them.

<img width="192" height="50" alt="processes4planet_full_color_microform" src="https://github.com/user-attachments/assets/5d2ad459-7662-4449-a2dc-1ca6eecbe106" /> 
<img width="224" height="50" alt="EN_FundedbytheEU_RGB_POS" src="https://github.com/user-attachments/assets/3c878e4d-c1cc-4cde-ad80-eb7059dd011b" />
