# How to Create Pecha in OpenPecha

1. Use [Metadata](https://github.com/OpenPecha-dev/openpecha-toolkit/blob/0265d00bdc4a13d326e798541b5d52a03b7e407f/openpecha/core/layer.py#L64) class to create metadata
here is an example
1. Use [Layer](https://github.com/OpenPecha-dev/openpecha-toolkit/blob/0265d00bdc4a13d326e798541b5d52a03b7e407f/openpecha/core/layer.py#L41) to create layer 
1. Use [OpenPechaFS](https://github.com/OpenPecha-dev/openpecha-toolkit/blob/0265d00bdc4a13d326e798541b5d52a03b7e407f/openpecha/core/pecha.py#L83) to create pecha

Here is example to create pecha
```python
from openpecha.core.layer import InitialCreationEnum, Layer, LayerEnum, MetaData
from openpecha.core.pecha import OpenPechaFS

openpecha = OpenPechaFS(
        base={"v001": "this is base"},
        layers={
            "v001": {
                LayerEnum.citation: Layer(
                    annotation_type=LayerEnum.citation,
                    revision="00001",
                    annotations={},
                )
            }
        },
        meta=MetaData(initial_creation_type=InitialCreationEnum.ebook),
    )

openpecha.save(tmpdirname)
```
