# oficina-de-dados-mi-emap

 Oficina de dados de MI @EMAP a ser aplicada como parte de avaliação individual.

## Como deixar um bucket para acesso publico

### abrir para página estática

### Bucket policy

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Statement1",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::oficina-0973/*"
        }
    ]
}
```

Fim - só abrir a URL...

### se quiser usar cache - cloud front

É só habilitar o cloud front escolhendo o bucket - tudo default - exceto o "do not use security" , para não habilitar waf.

Apontar diretamente para a pasta, pois não há index.html nas pastas.

https://d2pxua7zw5gx7n.cloudfront.net/opendatasus/mg/covid-vac-mg-1.csv

### Arquivo de população

Cabeçalho
UF;CODUF;CODMUNIC;NOMEMUNICÍPIO;POPULAÇÃOESTIMADA

Arquivo POP2021_20230710.csv

```sql
CREATE TABLE "oficina"."popestimada" WITH (
  partitioned_by = ARRAY['uf'],
  format = 'PARQUET',
  external_location ='s3://oficina-0973/ibge/popestimada/'
) AS
SELECT 
 coduf, 
 codmunic, 
 nomemunic, 
 cast (popestimada as bigint) as popestimada,
 uf
FROM "oficina"."populacao" WHERE UF !='UF';
```
