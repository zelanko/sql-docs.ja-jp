---
title: Kubernetes でのデータ永続化
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 のビッグ データ クラスター内のデータ永続化のしくみについて説明します。
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 24c90bfb8c99178e8ffa7822fba4bea709c536e1
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66800717"
---
# <a name="data-persistence-with-sql-server-big-data-cluster-on-kubernetes"></a>Kubernetes 上の SQL Server のビッグ データ クラスターでのデータ永続化

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[永続ボリューム](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)の記憶域の Kubernetes プラグイン モデルを提供します。 消費用途から、記憶域を提供する方法を抽象化されています。 そのため、独自の高可用性記憶域を移動し、SQL Server のビッグ データ クラスターに接続できます。 これにより、ストレージ、可用性、および必要なパフォーマンスの種類を完全に制御できるようにします。 Kubernetes では、さまざまな種類の Azure ディスク/ファイル、NFS、ローカルのストレージなどの記憶域ソリューションをサポートします。

## <a name="configure-persistent-volumes"></a>永続ボリュームを構成します。

使用してビッグ データの SQL Server クラスターは、これらの永続的なボリュームを使用する方法は、[ストレージ クラス](https://kubernetes.io/docs/concepts/storage/storage-classes/)します。 異なる種類のストレージ用のさまざまなストレージ クラスを作成し、ビッグ データ クラスターのデプロイ時にそれらを指定できます。 どのストレージ クラスと、プール レベルでは、どの目的に使用する永続ボリューム要求サイズを構成することができます。 ビッグ データの SQL Server クラスターを作成します[永続ボリューム要求](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims)永続ボリュームを必要とする各コンポーネントの指定されたストレージ クラスの名前を使用します。 ポッドに対応する永続的なボリュームをマウントします。 

## <a name="configure-big-data-cluster-storage-settings"></a>ビッグ データ クラスター記憶域の設定を構成します。

その他のカスタマイズと同様に、する設定を指定できます記憶域クラスターの構成ファイルに各プールとコントロール プレーンのデプロイ時にします。 場合は、コントロール プレーンのストレージ設定が使用され、プールの仕様では、記憶域の構成設定はありません。 これは、仕様に含めることができる記憶域の構成セクションのサンプルを示します。

```json
    "storage": 
    {
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
```

ビッグ データ クラスターのデプロイでは、永続的なストレージを使用して、データ、メタデータ、およびさまざまなコンポーネントのログを格納します。 展開の一部として作成された永続ボリューム要求のサイズをカスタマイズできます。 ストレージ クラスを使用するために推奨ベスト プラクティスとして、*保持*[回収ポリシー](https://kubernetes.io/docs/concepts/storage/storage-classes/#reclaim-policy)します。

> [!NOTE]
> CTP 3.0 では、記憶域の構成設定の投稿の展開を変更できません。 また、のみ`ReadWriteOnce`クラスター全体のアクセス モードがサポートされています。

> [!WARNING]
> 永続的な記憶域のない実行中は、テスト環境で作業できますが、非機能的なクラスターになる可能性があります。 ポッドが再起動するとクラスター メタデータ、またはユーザー データは完全に失われます。 この構成で実行をお勧めしません。 

[記憶域構成](#config-samples)ストレージの SQL Server ビッグ データ クラスター デプロイの設定を構成する方法の例についてを説明します。

## <a name="aks-storage-classes"></a>AKS のストレージ クラス

AKS が付属して[2 つの組み込みストレージ クラス](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv)**既定**と**管理されている premium**に動的プロビジョナーと共にします。 これらのいずれかを指定するか、永続的なストレージが有効になっているとビッグ データ クラスターをデプロイするため、独自のストレージ クラスを作成します。 既定で組み込みの aks クラスターの構成ファイルに*aks の開発-test.json*を使用する永続的なストレージ構成が付属して**既定**ストレージ クラス。

> [!WARNING]
> 組み込みストレージ クラスで作成された永続ボリューム**既定**と**管理されている premium**回収ポリシーを持つ*削除*します。 時に、SQL Server のビッグ データ クラスターも、削除、永続ボリューム要求は削除され、永続的なボリュームもを取得します。 使用してカスタムのストレージ クラスを作成する**azure ディスク**で privioner、*保持*ように、ポリシーを再利用[この](https://docs.microsoft.com/en-us/azure/aks/concepts-storage#storage-classes)記事。


## <a name="minikube-storage-class"></a>Minikube ストレージ クラス

呼ばれる組み込みストレージ クラスが付属して Minikube**標準**その動的プロビジョナーと共にします。 組み込みの構成ファイルを minikube *minikube-開発-test.json*に記憶域の構成設定、コントロール プレーンの仕様の。すべてのプール仕様には、同じ設定が適用されます。 またこのファイルのコピーをカスタマイズし、minikube でビッグ データ クラスターのデプロイに使用できます。 手動で、カスタムのファイルを編集しを実行する特定のプール、ワークロードに対応するために、永続ボリューム要求のサイズを変更することができます。 または、[記憶域構成](#config-samples)を使用して行う方法の例のセクションを編集します*mssqlctl*コマンド。

## <a name="kubeadm-storage-classes"></a>Kubeadm ストレージ クラス

Kubeadm は、組み込みストレージ クラスが付属していません。 独自のストレージ クラスとローカル ストレージまたは、優先のプロビジョナーをなどを使用して永続的なボリュームを作成する必要があります[ルーク](https://github.com/rook/rook)します。 その場合は、設定、 **className**構成した記憶域クラスへ。 

> [!NOTE]
>  組み込みの展開構成ファイルで*kubeadm kubeadm dev test.json*データとログの記憶域の指定されたストレージ クラス名はありません。 、展開前に、構成ファイルをカスタマイズし、className それ以外の場合は、配置前の検証の失敗の値を設定する必要があります。 展開では、必要な永続的なボリュームではなく、ストレージ クラスの存在をチェックする検証の手順もあります。 に応じて、クラスターのスケールのための十分なボリュームを作成することを確認する必要があります。 既定のクラスター サイズの CTP 3.0 では、少なくとも 23 のボリュームを作成する必要があります。 [ここで](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu)ローカル プロビジョナーを使用して永続的なボリュームを作成する方法の例を示します。


## <a name="customize-storage-configurations-for-each-pool"></a>各プールの記憶域構成をカスタマイズします。

すべてのカスタマイズの組み込みのコピーを作成する必要があります最初に使用する構成ファイルにします。 次のコマンドでのコピーを作成するなど、 *aks の開発-test.json*現在のディレクトリに展開構成ファイル。

```bash
mssqlctl cluster config init --src aks-dev-test.json --target custom.json
```

次に、いずれか、手動で編集して、構成ファイルをカスタマイズできますか、使用することができます*mssqlctl クラスター構成セクション セット*コマンド。 このコマンドのセットは jsonpath および jsonpatch ライブラリの組み合わせを使用して、構成ファイルを編集する方法を提供します。

### <a name="configure-size"></a>サイズを構成します。

既定では、各クラスターのプロビジョニングのポッドのプロビジョニングされた永続ボリューム要求のサイズは、10 GB が。 クラスターを展開する前に、カスタム構成ファイルで実行するワークロードに対応するためには、この値を更新することができます。

次の例は、100 Gi に記憶域プールに格納されたデータの永続ボリューム要求のサイズのみを更新します。 [ストレージ] セクションは、このコマンドを実行する前に、記憶域プールの構成ファイルに存在する必要がありますに注意してください。

```bash
mssqlctl cluster config section set -c custom.json -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.storage.data.size=100Gi"
```

次の例は、永続ボリューム要求のすべてのプールのサイズを 32 Gi に更新します。

```bash
mssqlctl cluster config section set -c custom.json -j "$.spec.controlPlane.spec.storage.data.size=32Gi"
```

### <a id="config-samples"></a> ストレージ クラスを構成します。

次の例では、コントロール プレーンのストレージ クラスを変更する方法を示します。

```bash
mssqlctl cluster config section set -c custom.json -j "$.spec.controlPlane.spec.storage.data.className=<yourStorageClassName>"
```

別のオプションは、カスタム構成ファイルを手動で編集や記憶域プールのストレージ クラスを変更する次の例のような jsonpatch を使用します。 作成、 *patch.json*にこのコンテンツのファイル。

```json
{
  "patch": [
    {
      "op": "add",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec.storage",
      "value": {
          "data": {
            "className": "default",
            "accessMode": "ReadWriteOnce",
            "size": "100Gi"
          },
          "logs": {
            "className": "default",
            "accessMode": "ReadWriteOnce",
            "size": "32Gi"
          }
        }
      }
  ]
}
```

修正プログラム ファイルを適用します。 使用*mssqlctl クラスター構成セクション セット*の JSON の修正プログラム ファイルの変更を適用するコマンド。 次の例では、ターゲット展開構成ファイルの custom.json に patch.json ファイルが適用されます。

```bash
mssqlctl cluster config section set -c custom.json -p ./patch.json
```

## <a name="next-steps"></a>次のステップ

Kubernetes でのボリュームに関する詳細なドキュメントを参照してください、[ボリューム上の Kubernetes のドキュメント](https://kubernetes.io/docs/concepts/storage/volumes/)します。

ビッグ データの SQL Server クラスターの展開に関する詳細については、次を参照してください。[を Kubernetes クラスターのビッグ データ、SQL Server をデプロイする方法](deployment-guidance.md)します。

