# Break down a notebook into _nbdev_ portable project
> interview task: break down a notebook into a portable, collaborative & easily deployable project. 


The initial project is a recommendation tool that is ready to be deployed.


Taking [this example](https://info.crunchydata.com/blog/recommendation_engine_in_postgres_with_pandas_and_python), we would like to deploy it server-side on our PostgreSQL server by embedding it into a simple python function.


To deploy it according to the best practice we'll break it down into a [_nbdev_](https://nbdev.fast.ai) project. This will allow us to continue developing the core components of our recommendations with collaborative jupyter notebooks : 
* [features_store notebooks](https://github.com/Pyth314/mle-2020/blob/main/mle-2020/00_features_store.ipynb) : for getting cleaned data & features for our recommendations
* [similarities](https://github.com/Pyth314/mle-2020/blob/main/mle-2020/01_similarities.ipynb) notebooks : where we develop the notions of similarity for our recommendations 
* [recommendation](https://github.com/Pyth314/mle-2020/blob/main/mle-2020/02_recommendation.ipynb): the way we deploy/access our recommendations

## Install

`pip install -e .`

## How to use

Getting the recommendation for `user_id 999` with the `dot_product_similarity`

```python
from moviesrec.features_store import movies , ratings , users , genre_and_title_cols , genre_cols
from moviesrec.similarities import dot_product_similarity
from moviesrec.recommendation import get_recommendations
```

```python
get_recommendations(user_id=999 , similarity = dot_product_similarity(movies[genre_cols]))
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>similarity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>166</td>
      <td>First Knight</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1451</td>
      <td>Smilla's Sense of Snow</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>503</td>
      <td>Perfect World, A</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3197</td>
      <td>Man Bites Dog (C'est arriv� pr�s de chez vous)</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1458</td>
      <td>Devil's Own, The</td>
      <td>2.0</td>
    </tr>
  </tbody>
</table>
</div>


