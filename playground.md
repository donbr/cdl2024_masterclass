Follow the instructions for the [Senzing ER playground](https://senzing.dockter.com/files/presentations/jupyter-sandbox.mp4),
developed by Michael Dockter:
<https://github.com/senzing-garage/playground>

```bash
docker run -it --name senzing-playground -p 8260:8260 -p 8261:8261 --rm senzing/playground
```

Once this is downloaded and running, then we'll run ER to merge
[three small datasets](https://www.youtube.com/watch?v=mY55S6a9Iok) together:
<http://localhost:8260/jupyter/lab/tree/python/senzing_load_truthsets.ipynb>

  * explore the `customers`, `reference`, `watchlist` datasets
  * inspect the `"Robert Smith"` entity
  * note how ER generates graph elements: entities, relations, properties

Next we'll work with open data for tracking sanctioned organizations
and _ultimate beneficial ownership_ connections:
<http://localhost:8260/jupyter/lab/tree/python/senzing_load_user_data.ipynb>

  * load datasets from <https://github.com/Kineviz/senzing_starter_kit>
  * show the merge of [OpenSanctions](https://www.opensanctions.org/) and [Open Ownership](https://www.openownership.org/en/)
  * inspect the `"Abassin Badshah"` entity
  * compare with the related graph visualization: <https://derwen.ai/s/khj9#43>
