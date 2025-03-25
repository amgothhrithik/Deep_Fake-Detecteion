#### ViTImageProcessor
- It is a class designed to handle image preprocessing for ViT models.
- `from_pretrained("...")` -
   - loads the pretrained image processor with appropriate config for a specific ViT model.
   - With this, we dont need to manually define resizing, normalization or cropping parameters.

####  load_dataset("imagefolder", data_dir=dataset_test_path)
- "imagefolder" is a sp. type of dataset in HuggingFace to load images from a directory.
- It automatically assigns labels(numeric) in order if there are diff folders belonging to diff classes.

#### transforms.Compose
- It is used to tranform the image for data Augmnetation.

#### dataset.map(transform_images)
- It is a mtd provided by datasets library to apply transformation and preprocessing to the dataset defined inside the function transform_images.
- In our case, we apply data augmentation for 35% of the dataset and apply preprocessing with ViTImageProcessor.

#### ViTForImageClassification
- It is a Pytorch model class fined for image classification tasks.It consists of :
  1. ViT encoder that processes image patches.
    - Image Patches => They are smaller region of the whole image(similar to words in NLP) and they are processed using self-attention mechanism.
    - Before sending patches into self-attention, they are flattened into 1-D vector.
    - This flattened is passed into trainable projection layer which is a fully connected linear layer.
    - This helps i converting each patch into a meaningful numerical representation.
  2. A classification head that maps features to class probabilities.
- `.from_pretrained("google/vit-base-patch16-224")`-
    - Loads model architecture
    - Loads pretrained weights
  
