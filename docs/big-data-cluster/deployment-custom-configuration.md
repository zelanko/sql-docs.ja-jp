---
title: 展開を構成します。
titleSuffix: SQL Server big data clusters
description: 構成ファイルでビッグ データ クラスターのデプロイをカスタマイズする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ccd7b0955cbeaa22f10a2b81515d7afd892e135e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958444"
---
# <a name="configure-deployment-settings-for-big-data-clusters"></a>ビッグ データ クラスターのデプロイ設定を構成します。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

クラスター展開の構成ファイルをカスタマイズするには、VSCode など、任意の JSON 形式エディターを使用できます。 これらの編集自動化のため、スクリプトを使用して、 **mssqlctl bdc 構成セクション**コマンド。 この記事では、展開構成ファイルを変更することでビッグ データ クラスターのデプロイを構成する方法について説明します。 これは、さまざまなシナリオの構成を変更する方法の例を示します。 展開構成ファイルを使用する方法の詳細については、次を参照してください。、[デプロイ ガイダンス](deployment-guidance.md#configfile)します。

## <a name="prerequisites"></a>必須コンポーネント

- [インストール mssqlctl](deploy-install-mssqlctl.md)します。

- このセクションの例のそれぞれは、標準の構成ファイルの 1 つのコピーを作成したと仮定します。 詳細については、次を参照してください。[カスタム構成ファイルを作成](deployment-guidance.md#customconfig)です。 たとえば、次のコマンドはというディレクトリを作成します。`custom`既定値に基づく JSON の展開構成ファイルを格納している**aks dev/test**構成。

   ```bash
   mssqlctl bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a> クラスター名の変更

クラスター名は、ビッグ データ クラスターのデプロイで作成される Kubernetes 名前空間名の両方です。 これは、展開構成ファイルの次の部分で指定されます。

```json
"metadata": {
    "kind": "Cluster",
    "name": "mssql-cluster"
},
```

次のコマンドにキー/値ペアの送信、 **- json 値**ビッグ データ クラスター名を変更するパラメーター**テスト クラスター**:

```bash
mssqlctl bdc config section set --config-profile custom -j "metadata.name=test-cluster"
```

> [!IMPORTANT]
> ビッグ データ クラスターの名前は小文字英数字文字、空白のみである必要があります。 すべての Kubernetes ・ アーティファクト (コンテナー、ポッド、ステートフルのセット、サービスなど)、クラスターのクラスターと同じ名前を持つ名前空間に作成されます名を指定します。

## <a id="ports"></a> エンドポイントのポートを更新します。

エンドポイントは、コントロール プレーンは、個々 のプールの場合と同様に定義されます。 構成ファイルの次の部分は、コントロール プレーンのエンドポイントの定義を示しています。

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

次の例では、インライン JSON を使用して、用のポートを変更する、**コント ローラー**エンドポイント。

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.controlPlane.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a> プールのレプリカを構成します。

プールごとに、記憶域プールなどの特性は、構成ファイルで定義されます。 たとえば、次の部分は、記憶域プールの定義を示しています。

```json
"pools": [
    {
        "metadata": {
            "kind": "Pool",
            "name": "default"
        },
        "spec": {
            "type": "Storage",
            "replicas": 2,
            "storage": {
               "data": {
                  "className": "default",
                  "accessMode": "ReadWriteOnce",
                  "size": "15Gi"
               },
               "logs": {
                  "className": "default",
                  "accessMode": "ReadWriteOnce",
                  "size": "10Gi"
               }
           },
        }
    }
]
```

プールのインスタンスの数を構成するには変更することによって、**レプリカ**各プールの値。 次の例では、インライン JSON を使用して、ストレージとデータのプールをこれらの値を変更する`10`と`4`それぞれ。

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.replicas=10"
mssqlctl bdc config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Data"")].spec.replicas=4"
```

## <a id="storage"></a> 記憶域を構成します。

ストレージ クラスと各プールに使用される特徴を変更することもできます。 次の例では、カスタム ストレージ クラスを記憶域プールに割り当てられ、100 gb のデータを格納するため、永続ボリューム要求のサイズを更新します。 このセクションを使用して設定を更新する構成ファイルである、 *mssqlctl bdc 構成セット*コマンドで、以下の修正プログラム ファイルを使用して、このセクションを追加する方法を参照してください。

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.storage.data.className=storage-pool-class"
mssqlctl bdc config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.storage.data.size=32Gi"
```

> [!NOTE]
> 構成ファイルに基づいて**kubeadm-開発/テスト**、各プールが、これは手動で追加する必要な場合のストレージの定義を持たない。

記憶域の構成の詳細については、次を参照してください。[を Kubernetes クラスターのビッグ データ、SQL Server でのデータ永続化](concept-data-persistence.md)します。

## <a id="sparkstorage"></a> Spark なしの記憶域を構成します。

Spark せずに実行し、個別の spark プールを作成するには、記憶域プールを構成することもできます。 ストレージのスケール spark コンピューティング パワー独立にできます。 Spark のプールを構成する方法を確認するには、次を参照してください。、[修正プログラム ファイルの例の JSON](#jsonpatch)この記事の最後にします。

このセクションを使用して設定を更新する構成ファイルである、`mssqlctl cluster config set command`します。 次の JSON の修正プログラム ファイルは、これを追加する方法を示します。

既定で、 **includeSpark**設定は、追加する必要がありますので、true に、記憶域プールが設定されて、 **includeSpark**フィールドを変更するには、記憶域の構成。

```bash
mssqlctl cluster config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Storage"")].includeSpark=false"
```

## <a id="podplacement"></a> Kubernetes ラベルを使用してポッドの配置を構成します。

さまざまな種類のワークロード要件に対応するために特定のリソースがある Kubernetes ノード上のポッドの配置を制御できます。 たとえば、記憶域プールのポッドは多くのストレージをノードに配置されますか、master の SQL Server インスタンスは以上の CPU とメモリ リソースを持つノードに配置されてことを確認します。 さまざまな種類のハードウェアの異種 Kubernetes クラスターを最初に構築するこの例では、し[ノード ラベルを割り当てる](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)それに応じて。 ビッグ データ クラスターの展開時に、クラスターの展開構成ファイルでプール レベルで同じラベルを指定できます。 Kubernetes の指定されたラベルに一致するノードにポッド関係付けることができますが処理します。

次の例では、SQL Server のマスター インスタンスのノードのラベル設定に含めるカスタム構成ファイルを編集する方法を示します。 あることに注意してくださいありません*nodeLabel*カスタム構成ファイルを手動で編集するか、または修正プログラム ファイルを作成し、カスタム構成ファイルに適用する必要があります組み込みの構成のキー。

という名前のファイルを作成する**patch.json**次の内容の現在のディレクトリ。

```json
{
  "patch": [
     {
      "op": "add",
      "path": "$.spec.pools[?(@.spec.type == 'Master')].spec",
      "value": {
      "nodeLabel": "<yourNodeLabel>"
       }
    }
  ]
}
```

```bash
mssqlctl bdc config section set --config-profile custom -p ./patch.json
```

## <a id="jsonpatch"></a> JSON の修正プログラム ファイル

JSON の修正プログラム ファイルは、一度に複数の設定を構成します。 JSON パッチの詳細については、次を参照してください。 [Python での JSON パッチ](https://github.com/stefankoegl/python-json-patch)と[JSONPath オンライン エバリュエーター](https://jsonpath.com/)します。

次**patch.json**ファイルは、次の変更を実行します。

- 1 つのエンドポイントのポートを更新します。
- すべてのエンドポイントを更新 (**ポート**と**serviceType**)。
- コントロール プレーンの記憶域を更新します。 これらの設定は、プール レベルでオーバーライドされない限り、すべてのクラスター コンポーネントに適用されます。
- コントロール プレーンの記憶域内のストレージ クラス名を更新します。
- 記憶域プールのプール ストレージの設定を更新します。
- 記憶域プールの Spark の設定を更新します。
- 2 つのレプリカのクラスターで spark プールを作成します。

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.controlPlane.spec.endpoints[?(@.name=='Controller')].port",
      "value": 30000
    },
    {
      "op": "replace",
      "path": "spec.controlPlane.spec.endpoints",
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
    },
    {
      "op": "replace",
      "path": "spec.controlPlane.spec.controlPlane",
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
    },
    {
      "op": "replace",
      "path": "spec.controlPlane.spec.storage.data.className",
      "value": "managed-premium"
    },
    {
      "op": "add",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec.storage",
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
    },
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
    },
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
> 構造体と、展開構成ファイルを変更するためのオプションの詳細については、次を参照してください。[ビッグ データ クラスターの展開構成ファイル リファレンス](reference-deployment-config.md)します。

使用**mssqlctl bdc 構成セクション セット**パッチの JSON ファイルの変更を適用します。 次の例では、適用、 **patch.json**ファイル ターゲットの展開構成ファイルを**custom.json**します。

```bash
mssqlctl bdc config section set --config-profile custom -p ./patch.json
```

## <a name="next-steps"></a>次の手順

ビッグ データ クラスター展開で構成ファイルの使用についての詳細については、次を参照してください。[ビッグ データの SQL Server をデプロイする方法を Kubernetes クラスターの](deployment-guidance.md#configfile)します。
