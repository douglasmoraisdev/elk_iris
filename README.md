# elk_iris - A Elasticsearch, Logstash, Kibana stack for Twitter Post Monitoring

## Subindo o stack

>$ docker-compose up

## Kibana Dashboard

> http://localhost:5601/app/kibana

## Configurando o Logstash
Em `logstash/pipeline/twitter.conf`:

```
input {
  twitter {
    id => "twitter_input"
    consumer_key => "<YOUR_CONSUMER_KEY>"
    consumer_secret => "<YOUR_SECRET>"
    oauth_token => "<YOUR_OAUTH_TOKEN>"
    oauth_token_secret => "<YOU_ALREADY_KNOW...>"
    ignore_retweets => true
    keywords => ["some_key_words"]
  }

}

filter {}

output {
  elasticsearch {
    hosts => ["http://elasticsearch:9200"]
    index => "twitter_input"
  }
}

```
