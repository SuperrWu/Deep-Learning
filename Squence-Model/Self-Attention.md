# Self-Attention
## Target
![image](https://user-images.githubusercontent.com/94330800/144342859-736956fd-cc97-4b3e-a04d-380f76235008.png)

The input sequence becomes another output sequence.

## Compute single output b

![image](https://user-images.githubusercontent.com/94330800/144341422-a27f6745-0cdb-4632-8e2e-e53421e7ad7c.png)
### Find relevance of input sequence

* dot product

![image](https://user-images.githubusercontent.com/94330800/144341622-769e8bb0-4f9b-4379-b88d-93e4706a3869.png)

dot product of Q and K.

* Additive

![image](https://user-images.githubusercontent.com/94330800/144341676-a901a948-3432-4ee2-9f50-7a24979fdadf.png)

concatenate input vector, and then get transforemed vector after the activation function (usually softmax).

### compute a
![image](https://user-images.githubusercontent.com/94330800/144342399-648085ba-4982-4c00-96cd-75d0526d2778.png)

a = dot product of query and key.

### compute b
![image](https://user-images.githubusercontent.com/94330800/144342738-fa0f41af-9c46-481f-b7e1-35ed4331c57d.png)

b = attention score * value

## Equations of self-attention
![image](https://user-images.githubusercontent.com/94330800/144343723-c315ce19-bd30-4012-8cd4-aa24aaf34dd5.png)

![image](https://user-images.githubusercontent.com/94330800/144343911-9b0cfead-cbf2-4519-806a-586632f41b74.png)

![image](https://user-images.githubusercontent.com/94330800/144344097-df3e9967-c3c5-408e-b15d-485843e00760.png)


# Muti-head Attention

different q to different relevant.

![image](https://user-images.githubusercontent.com/94330800/144344877-a882dcb2-74db-46a8-a50c-21abdcd8794b.png)

![image](https://user-images.githubusercontent.com/94330800/144344936-3d6f98fc-e98d-4379-891a-f2d173a04632.png)

## Limitations

no position information in self-attention.

## Position encoding


## Relationship between CNN and Self-Attention

![image](https://user-images.githubusercontent.com/94330800/144346126-c694f2d9-9ebd-45c0-8b89-fccb50d2f4c1.png)

## Relationship between RNN and Self-Attention

![image](https://user-images.githubusercontent.com/94330800/144346866-883b939c-a3e8-4fb1-8cb0-6edc49bce05c.png)

