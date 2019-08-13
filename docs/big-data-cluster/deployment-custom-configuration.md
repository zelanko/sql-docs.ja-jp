---
title: 展開を構成する
titleSuffix: SQL Server big data clusters
description: 構成ファイルを使用してビッグ データ クラスターの展開をカスタマイズする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cae2c216245fdb6483b3ad07a88b3517c38550bd
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68470750"
---
# <a name="configure-deployment-settings-for-big-data-clusters"></a>ビッグ データ クラスターの展開設定を構成する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

クラスターの展開構成ファイルをカスタマイズするには、VSCode など、任意の JSON 形式エディターを使用できます。 自動化のためにこれらの編集をスクリプト化するには、**azdata bdc config** コマンドを使用します。 この記事では、展開構成ファイルを変更してビッグ データ クラスターの展開を構成する方法について説明します。 さまざまなシナリオについて構成の変更方法の例を示します。 展開に構成ファイルを使用する方法の詳細詳細については、「[展開のガイダンス](deployment-guidance.md#configfile)」を参照してください。

## <a name="prerequisites"></a>Prerequisites

- [azdata をインストールします](deploy-install-azdata.md)。

- このセクションの各例では、標準構成のいずれかのコピーを作成済みであることを前提としています。 詳細については、[カスタム構成の作成](deployment-guidance.md#customconfig)に関する記事を参照してください。 たとえば、次のコマンドでは、既定値の **aks-dev-test** 構成に基づいて、2 つの JSON 展開構成ファイル (**cluster.json** と **control.json**) を含む `custom` というディレクトリが作成されます。

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a> クラスター名を変更する

クラスター名は、ビッグ データ クラスターと、展開時に作成される Kubernetes 名前空間の両方の名前です。 これは **cluster.json** 展開構成ファイルの次の部分で指定されます。

```json
"metadata": {
    "kind": "Cluster",
    "name": "mssql-cluster"
},
```

次のコマンドでは、キーと値のペアを **--json-values** パラメーターに送信し、ビッグ データ クラスター名を **test-cluster** に変更します。

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "metadata.name=test-cluster"
```

> [!IMPORTANT]
> ビッグ データ クラスターの名前は、小文字の英数字のみを使用し、スペースを含めない必要があります クラスターのすべての Kubernetes 成果物 (コンテナー、ポッド、ステートフル セット、サービス) は、指定したクラスター名と同じ名前の名前空間に作成されます。

## <a id="ports"></a> エンドポイント ポートを更新する

エンドポイントは、**control.json** のコントローラー用と、**cluster.json** の対応するセクションのゲートウェイと SQL Server マスター インスタンス用に定義されます。 **control.json** 構成ファイルの次の部分は、コントローラーのエンドポイント定義を示しています。

```json
"endpoints": [
    {
        "name": "Controller",
        "serviceType": "LoadBalancer",
        "port": 30080
    },
    {
        "name": "ServiceProxy",
        "serviceType": "LoadBalancer",
        "port": 30777
    }
]
```

次の例では、インライン JSON を使用して **controller** エンドポイントのポートを変更します。

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a> プールのレプリカを構成する

記憶域プールなどの各プールの特性は、**cluster.json** 構成ファイルに定義されます。 たとえば、**cluster.json** の次の部分は、記憶域プールの定義を示しています。

```json
"pools": [
   {
       "metadata": {
           "kind": "Pool",
           "name": "default"
       },
       "spec": {
           "type": "Storage",
           "replicas": 2
       }
   }
]
```

プール内のインスタンスの数を構成するには、各プールの **replicas** 値を変更します。 次の例では、インライン JSON を使用して、記憶域プールとデータ プールのこれらの値をそれぞれ `10` と `4` に変更します。

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Storage"")].spec.replicas=10"
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Data"")].spec.replicas=4"
```

## <a id="storage"></a> 記憶域を構成する

各プールに使用される記憶域クラスと特性を変更することもできます。 次の例では、カスタム記憶域クラスを記憶域プールに割り当て、データを保存する永続ボリューム要求のサイズを 100Gb に更新します。 まず、次のように、*type* と *replicas* に加えて新しい *storage* セクションを含む patch.json ファイルを作成します

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
      "value": {
        "storage":{
        "data":{
                "size": "100Gi",
                "className": "myStorageClass",
                "accessMode":"ReadWriteOnce"
                },
        "logs":{
                "size":"32Gi",
                "className":"myStorageClass",
                "accessMode":"ReadWriteOnce"
                }
                },
        "type":"Storage",
        "replicas":2
      }
    }
  ]
}
```

次に **azdata bdc config patch** コマンドを使用して **cluster.json** 構成ファイルを更新できます。
```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json
```

> [!NOTE]
> **kubeadm-dev-test** に基づく構成ファイルには、各プールの記憶域の定義はありませんが、必要に応じて上のプロセスを使用して追加できます。

記憶域構成の詳細については、「[Kubernetes 上の SQL Server ビッグ データ クラスターでのデータ永続化](concept-data-persistence.md)」を参照してください。

## <a id="sparkstorage"></a> Spark を使用せずに記憶域プールを構成する

また、Spark を使用せずに実行し、別の Spark プールを作成するように記憶域プールを構成することもできます。 こうすると、記憶域に依存せず、Spark コンピューティングの機能を拡張することができます。 Spark プールを構成する方法については、この記事の末尾にある [JSON 修正プログラム ファイルの例](#jsonpatch)を参照してください。



既定で記憶域プールの **includeSpark** 設定は true に設定されているため、変更するには記憶域の構成に **includeSpark** フィールドを追加する必要があります。 次の JSON 修正プログラム ファイルは、これを追加する方法を示しています。

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
      "value": {
       "type":"Storage",
       "replicas":2,
       "includeSpark":false
      }
    }
  ]
}
```

```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json
```

## <a id="podplacement"></a> Kubernetes ラベルを使用してポッドの配置を構成する

Kubernetes ノード上で特定のリソースを持つポッドの配置を制御することで、さまざまな種類のワークロード要件に対応できます。 たとえば、記憶域プール ポッドを記憶域が多いノードに配置したり、SQL Server マスター インスタンスを CPU およびメモリ リソースが高いノードに配置したりすることができます。 この場合、まず異なる種類のハードウェアが混在する Kubernetes クラスターを構築してから、それに応じて[ノード ラベルを割り当てます](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)。 ビッグ データ クラスターを展開する際に、クラスター展開構成ファイルのプール レベルで同じラベルを指定できます。 Kubernetes では、ノード上の指定されたラベルに一致するポッドの関連付けが処理されます。

次の例は、SQL Server マスター インスタンスのノード ラベル設定を含むようにカスタム構成ファイルを編集する方法を示しています。 組み込みの構成には *nodeLabel* キーがないため、カスタム構成ファイルを手動で編集するか、修正プログラム ファイルを作成してカスタム構成ファイルに適用する必要があります。

現在のディレクトリに次の内容の **patch.json** という名前のファイルを作成します。

```json
{
  "patch": [
     {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Master')].spec",
      "value": {
    "type": "Master",
        "replicas": 1,
        "hadrEnabled": false,
        "endpoints": [
            {
             "name": "Master",
             "serviceType": "NodePort",
             "port": 31433
            }
          ],
        "nodeLabel": "<yourNodeLabel>"
       }
    }
  ]
}
```

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a id="jsonpatch"></a> JSON 修正プログラム ファイル

JSON 修正プログラム ファイルによって、複数の設定が一度で構成されます。 Json 修正プログラムの詳細については、[Python の JSON 修正プログラム](https://github.com/stefankoegl/python-json-patch)と [JSONPath Online Evaluator](https://jsonpath.com/) のページを参照してください。

次の **patch.json** ファイルでは、次の変更が実行されます。

- **control.json** で、1 つのエンドポイントのポートを更新します。
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "$.spec.endpoints[?(@.name=='Controller')].port",
          "value": 30000
        }   
      ]
    }
    ```

- **control.json** で、すべてのエンドポイント (**port** と **serviceType**) を更新します。
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.endpoints",
          "value": [
        {
          "serviceType": "LoadBalancer",
          "port": 30001,
          "name": "Controller"
        },
        {
          "serviceType": "LoadBalancer",
          "port": 30778,
          "name": "ServiceProxy"
        }
          ]
        }
      ]
    }
    ```

- **control.json** で、コントローラーの記憶域設定を更新します。 これらの設定は、プール レベルで上書きされない限り、すべてのクラスター コンポーネントに適用されます。
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.storage",
          "value": {
        "data": {
            "className": "managed-premium",
            "accessMode": "ReadWriteOnce",
            "size": "100Gi"
               },
        "logs": {
            "className": "managed-premium",
            "accessMode": "ReadWriteOnce",
            "size": "32Gi"
               }
           }
         }  
      ]
    }
    ```

- **control.json** で、記憶域クラス名を更新します。
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.storage.data.className",
          "value": "managed-premium"
        }   
      ]
    }
    ```

- **cluster.json** で、記憶域プールのプール記憶域設定を更新します。
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
          "value": {
        "type":"Storage",
        "replicas":2,
        "storage":{
        "data":{
            "size": "100Gi",
            "className": "myStorageClass",
            "accessMode":"ReadWriteOnce"
            },
        "logs":{
            "size":"32Gi",
            "className":"myStorageClass",
            "accessMode":"ReadWriteOnce"
            }
            }
         }
        }
      ]
    }
    ```

- **cluster.json** で、記憶域プールの Spark 設定を更新します。
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "$.spec.pools[?(@.spec.type == 'Storage')].hadoop.spark",
          "value": {
        "driverMemory": "2g",
        "driverCores": 1,
        "executorInstances": 3,
        "executorCores": 1,
        "executorMemory": "1536m"
          }
        }   
      ]
    }
    ```

- **cluster.json** で、2 つのインスタンスを持つ Spark プールを作成します。
    ```json
    {
      "patch": [
        {
          "op": "add",
          "path": "spec.pools/-",
          "value":
          {
        "metadata": {
          "kind": "Pool",
          "name": "default"
        },
        "spec": {
          "type": "Spark",
          "replicas": 2
        },
        "hadoop": {
          "yarn": {
            "nodeManager": {
              "memory": 12288,
              "vcores": 6
            },
            "schedulerMax": {
              "memory": 12288,
              "vcores": 6
            },
            "capacityScheduler": {
              "maxAmPercent": 0.3
            }
          },
          "spark": {
            "driverMemory": "2g",
            "driverCores": 1,
            "executorInstances": 2,
            "executorMemory": "2g",
            "executorCores": 1
          }
        }
          }
        } 
      ]
    }
    ```



> [!TIP]
> 展開構成ファイルを変更するための構造とオプションの詳細については、「[ビッグ データ クラスターの展開構成ファイル リファレンス](reference-deployment-config.md)」を参照してください。

**azdata bdc config** コマンドを使用して、JSON 修正プログラム ファイルに変更を適用します。 次の例では、**patch.json** ファイルをターゲットのデプロイ構成ファイルである **custom/cluster.json** に適用します。

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a name="next-steps"></a>次の手順

ビッグ データ クラスターの展開で構成ファイルを使用する方法の詳細については、「[Kubernetes に SQL Server ビッグ データ クラスターを展開する方法](deployment-guidance.md#configfile)」を参照してください。
