---
layout: single
permalink: /about/
---

Home automation enthusiast and software developer. I like to learn about new things more than finishing up an "exercise left for the reader".

{% highlight python %}
import mlflow
import openai

# Chat
with mlflow.start_run():
    info = mlflow.openai.log_model(
        model="gpt-3.5-turbo",
        task=openai.ChatCompletion,
        messages=[{"role": "user", "content": "Tell me a joke about {animal}."}],
        artifact_path="model",
    )
    model = mlflow.pyfunc.load_model(info.model_uri)
    df = pd.DataFrame({"animal": ["cats", "dogs"]})
    print(model.predict(df))
{% endhighlight %}
