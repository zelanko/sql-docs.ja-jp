---
title: デプロイの構成
titleSuffix: SQL Server big data clusters
description: 構成ファイルを使用してビッグデータクラスターの展開をカスタマイズする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d7559ecf9c7b17ca21c088ed531a347f88e89ee2
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419440"
---
# <a name="configure-deployment-settings-for-big-data-clusters"></a>ビッグデータクラスターの展開設定を構成する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

クラスターの配置構成ファイルをカスタマイズするには、VSCode などの任意の JSON 形式エディターを使用できます。 自動化のためにこれらの編集をスクリプト化するには、 **azdata bdc config**コマンドを使用します。 この記事では、展開構成ファイルを変更してビッグデータクラスターの展開を構成する方法について説明します。 さまざまなシナリオの構成を変更する方法の例を示します。 配置での構成ファイルの使用方法の詳細については、「[展開のガイダンス](deployment-guidance.md#configfile)」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

- [Azdata をインストール](deploy-install-azdata.md)します。

- このセクションの各例では、標準構成のいずれかのコピーが作成されていることを前提としています。 詳細については、「[カスタム構成を作成する](deployment-guidance.md#customconfig)」を参照してください。 たとえば、次のコマンドは、 `custom`既定の**aks**構成を基にしたという名前のディレクトリを作成します。このディレクトリには、**クラスター**の json と**control. json**が含まれています。

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a>クラスター名の変更

クラスター名は、ビッグデータクラスターの名前と、デプロイ時に作成される Kubernetes 名前空間の両方です。 これは、**クラスターの json**展開構成ファイルの次の部分で指定されています。

```json
"metadata": {
    "kind": "Cluster",
    "name": "mssql-cluster"
},
```

次のコマンドは、 **--json-values**パラメーターにキーと値のペアを送信して、ビッグデータクラスター名を**テストクラスター**に変更します。

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "metadata.name=test-cluster"
```

> [!IMPORTANT]
> ビッグデータクラスターの名前は、アルファベットの小文字のみで、スペースは使用できません。 クラスターのすべての Kubernetes アーティファクト (コンテナー、ポッド、ステートフル sets、services) は、指定したクラスター名と同じ名前の名前空間に作成されます。

## <a id="ports"></a>エンドポイントポートを更新する

エンドポイントは、コントローラーに対して定義されてい**ます。** また、ゲートウェイの場合は、**クラスター**の対応するセクションにある SQL Server マスターインスタンスです。 **コントロールの json**構成ファイルの次の部分は、コントローラーのエンドポイント定義を示しています。

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

次の例では、インライン JSON を使用して、**コントローラー**エンドポイントのポートを変更します。

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a>プールレプリカの構成

各プールの特性 (記憶域プールなど) は、**クラスターの json**構成ファイルで定義されています。 たとえば、クラスターの次の部分は、記憶域プールの定義を示して**います。**

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

プール内のインスタンスの数を構成するには、各プールの**レプリカ**の値を変更します。 次の例では、インライン JSON を使用して、ストレージとデータプール`10`の`4`これらの値をそれぞれとに変更します。

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Storage"")].spec.replicas=10"
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Data"")].spec.replicas=4"
```

## <a id="storage"></a>ストレージの構成

また、各プールに使用されるストレージクラスと特性を変更することもできます。 次の例では、カスタムストレージクラスを記憶域プールに割り当て、データを 100 Gb に格納するための永続ボリューム要求のサイズを更新します。 まず、*種類*と*レプリカ*に加えて、新しい*ストレージ*セクションを含む patch. json ファイルを作成します。

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

その後、 **azdata bdc**の構成パッチコマンドを使用して、**クラスターの json**構成ファイルを更新できます。
```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json
```

> [!NOTE]
> **Kubeadm**に基づく構成ファイルには、各プールのストレージ定義がありませんが、必要に応じて上記のプロセスを使用して追加することができます。

ストレージ構成の詳細については、「Kubernetes でのデータの永続化」を参照してください。 [SQL Server ビッグデータクラスターを使用](concept-data-persistence.md)してください。

## <a id="sparkstorage"></a>Spark を使用せずに記憶域プールを構成する

また、spark なしで実行するように記憶域プールを構成し、別の spark プールを作成することもできます。 これにより、ストレージに依存せずに spark コンピューティングの機能を拡張することができます。 Spark プールを構成する方法については、この記事の最後にある[JSON 修正プログラムファイルの例](#jsonpatch)を参照してください。



既定では、記憶域プールの [含まれている**駐車**] 設定は [true] に設定されているため、変更を行うには、[**格納] フィールド**をストレージ構成に追加する必要があります。 次の JSON 修正プログラムファイルは、このを追加する方法を示しています。

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

## <a id="podplacement"></a>Kubernetes ラベルを使用してポッド配置を構成する

さまざまな種類のワークロード要件に対応するために、特定のリソースを持つ Kubernetes ノードでポッド配置を制御できます。 たとえば、記憶域プールポッドがより多くの記憶域を持つノードに配置されていること、また SQL Server は CPU とメモリリソースが高いノードにマスターインスタンスが配置されていることを確認する必要がある場合があります。 この場合は、まず異なる種類のハードウェアで異種混在の Kubernetes クラスターを構築し、それに応じて[ノードラベルを割り当て](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)ます。 ビッグデータクラスターを展開するときに、クラスター展開構成ファイルのプールレベルで同じラベルを指定できます。 Kubernetes は、指定されたラベルに一致するノード上のポッドを関連付けに処理します。

次の例では、カスタム構成ファイルを編集して、SQL Server マスターインスタンスのノードラベル設定を含める方法を示します。 組み込みの構成に*Nodelabel*キーがないことに注意してください。カスタム構成ファイルを手動で編集するか、修正プログラムファイルを作成してカスタム構成ファイルに適用する必要があります。

次の内容を使用して、現在のディレクトリに**patch. json**という名前のファイルを作成します。

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

## <a id="jsonpatch"></a>JSON 修正プログラムファイル

JSON 修正プログラムファイルは、一度に複数の設定を構成します。 JSON 修正プログラムの詳細については、「 [Python の Json 修正プログラム](https://github.com/stefankoegl/python-json-patch)」および「 [Jsonpath Online エバリュエーター](https://jsonpath.com/)」を参照してください。

次の**更新プログラムの json**ファイルでは、次の変更が実行されます。

- コントロールの1つのエンドポイントのポートを更新し**ます。**
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

- コントロールのすべてのエンドポイント (**ポート**と**serviceType**) を更新し**ます**。
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

- **Control. json**のコントローラーのストレージ設定を更新します。 これらの設定は、プールレベルでオーバーライドされない限り、すべてのクラスターコンポーネントに適用されます。
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

- **Control. json**でストレージクラス名を更新します。
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

- **クラスター**の記憶域プールのプール記憶域設定を更新します。
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

- **クラスター**の記憶域プールの Spark 設定を更新します。
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

- **クラスター**内に2つのインスタンスを持つ spark プールを作成します。
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
> 展開構成ファイルを変更するための構造とオプションの詳細については、「[ビッグデータクラスターの展開構成ファイルリファレンス](reference-deployment-config.md)」を参照してください。

**Azdata bdc の構成**コマンドを使用して、JSON 修正プログラムファイルに変更を適用します。 次の例では、**修正プログラムの json**ファイルをターゲットの配置構成ファイルの**カスタム/クラスター**に適用します。

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a name="next-steps"></a>次の手順

ビッグデータクラスターの展開における構成ファイルの使用方法の詳細については、「 [Kubernetes でビッグデータクラスターを SQL Server デプロイする方法](deployment-guidance.md#configfile)」を参照してください。
