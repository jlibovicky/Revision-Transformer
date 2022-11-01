# Revision Transformer

We propose Revision Transformer (RiT) to easily and interactively revise large-scale Transformer models in order to align them with human preferences in an online and democratic fashion.

Run `main.py` to generate answers with contextualized inputs. Check arguments for further adjustments. Use `process.py` to process moral norms data into the right file format and to pre-generate embeddings for comparison. With `eval.py` you can evaluate the generated text with certain metrics.
A pipeline to preprocess the data could be:
```
python process.py --dataset norms --version agreement
```
Afterwards you can use
```
python main.py --type qna --nn 1 --thresh 0.875 --model_name T0-3B
```
for baseline answers and
```
python main.py --type qna --nn 1 --thresh 0.875 --model_name T0-3B --baseline True
```
for answers with RiT. For a multilingual approach, you could e.g. use
```
python main.py --type qna --nn 1 --thresh 0.45 --model_name bloom-3b --lang en
```
For the evaluation, you can use
```
python eval.py --type qna --nn 1 --thresh 0.875 --model_name T0-3B
```
Note, for the evaluation, both the baseline and RiT answers have to be generated beforehand.

## Data
Get data from `/storage-01/ml-ffriedrich/repositories/datasets/norms/` or `https://github.com/liweijiang/delphi/`

## Citation
If you like or use our work please cite us:
```bibtex
@article{friedrich2022RiT,
      title={Revision Transformers: Getting RiT of No-Nos}, 
      author={Felix Friedrich and Wolfgang Stammer and Patrick Schramowski and Kristian Kersting},
      year={2022},
      journal={arXiv preprint arXiv:2210.10332}
}
```
