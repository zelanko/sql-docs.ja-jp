---
title: Kubernetes でのデータの永続化
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグデータクラスターでのデータ永続化のしくみについて説明します。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9142836032acc5e302c947e1619d17b07faff683
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419472"
---
# <a name="data-persistence-with-sql-server-big-data-cluster-on-kubernetes"></a>Kubernetes 上の SQL Server ビッグデータクラスターでのデータ永続化

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[永続ボリューム](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)は、Kubernetes のストレージのプラグインモデルを提供します。 ストレージの提供方法は、その使用方法から抽象化されています。 そのため、独自の高可用性記憶域を使用して、SQL Server ビッグデータクラスターに接続することができます。 これにより、必要なストレージ、可用性、およびパフォーマンスの種類を完全に制御できます。 Kubernetes は、Azure ディスク/ファイル、NFS、ローカルストレージなどのさまざまな種類のストレージソリューションをサポートしています。

## <a name="configure-persistent-volumes"></a>永続ボリュームの構成

SQL Server ビッグデータクラスターがこれらの永続ボリュームを消費する方法は、[ストレージクラス](https://kubernetes.io/docs/concepts/storage/storage-classes/)を使用することです。 ストレージの種類ごとに異なるストレージクラスを作成し、ビッグデータクラスターの展開時に指定することができます。 プールレベルの目的に使用するストレージクラスと永続ボリューム要求のサイズを構成できます。 SQL Server ビッグデータクラスターは、永続ボリュームを必要とする各コンポーネントについて、指定されたストレージクラス名を持つ[永続ボリューム要求](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims)を作成します。 次に、対応する永続ボリュームをポッドにマウントします。 

## <a name="configure-big-data-cluster-storage-settings"></a>ビッグデータクラスターのストレージ設定を構成する

他のカスタマイズと同様に、各プールとコントロールプレーンのデプロイ時に、クラスター構成ファイルでストレージ設定を指定できます。 プールの仕様にストレージ構成設定がない場合は、コントロールプレーンのストレージ設定が使用されます。 これは、仕様に含めることができるストレージ構成セクションのサンプルです。

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

ビッグデータクラスターのデプロイでは、永続ストレージを使用して、さまざまなコンポーネントのデータ、メタデータ、およびログを格納します。 デプロイの一部として作成された永続的なボリューム要求のサイズをカスタマイズできます。 ベストプラクティスとして、ストレージクラスは、[回収ポリシー](https://kubernetes.io/docs/concepts/storage/storage-classes/#reclaim-policy)を*保持*して使用することをお勧めします。

> [!NOTE]
> CTP 3.2 では、配置後にストレージ構成設定を変更することはできません。 また、クラスター `ReadWriteOnce`全体のアクセスモードのみがサポートされています。

> [!WARNING]
> 永続的なストレージを使用せずに実行することは、テスト環境で動作しますが、機能しないクラスターになる可能性があります。 ポッドの再起動時に、クラスターのメタデータやユーザーデータが完全に失われます。 この構成ではを実行しないことをお勧めします。 

「[ストレージの構成](#config-samples)」セクションでは、SQL Server ビッグデータクラスターの展開で使用するストレージ設定を構成する方法の例を示します。

## <a name="aks-storage-classes"></a>AKS ストレージクラス

AKS には、 [2 つの組み込みストレージクラス](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv)の**既定**と**管理 premium**と、それらの動的プロビジョナーが付属しています。 これらのいずれかを指定することも、永続ストレージが有効になっているビッグデータクラスターをデプロイするための独自のストレージクラスを作成することもできます。 既定では、aks *aks*の組み込みのクラスター構成ファイルには、**既定**のストレージクラスを使用するための永続的なストレージ構成が付属しています。

> [!WARNING]
> 組み込みのストレージクラスを使用して作成された永続ボリュームでは、**既定**と管理された**Premium**が、*削除*のポリシーを回収します。 そのため、SQL Server ビッグデータクラスターを削除すると、永続ボリュームの要求が削除され、永続ボリュームも保持されます。 [この](https://docs.microsoft.com/en-us/azure/aks/concepts-storage#storage-classes)記事に示されているように、 **azure-disk** privioner と "回収を*保持*する" ポリシーを使用して、カスタムストレージクラスを作成できます。


## <a name="minikube-storage-class"></a>Minikube ストレージクラス

Minikube には、**標準**と呼ばれる組み込みのストレージクラスと、それに動的なプロビジョナーが付属しています。 Minikube *minikube*の組み込み構成ファイルには、コントロールプレーン仕様のストレージ構成設定が含まれています。すべてのプールの仕様に同じ設定が適用されます。 また、このファイルのコピーをカスタマイズし、minikube でのビッグデータクラスターのデプロイに使用することもできます。 カスタムファイルを手動で編集し、特定のプールに対する永続的なボリューム要求のサイズを変更して、実行するワークロードに対応することができます。 または、 *azdata*コマンドを使用して編集する方法の例については、「[ストレージの構成](#config-samples)」セクションを参照してください。

## <a name="kubeadm-storage-classes"></a>Kubeadm ストレージクラス

Kubeadm には、組み込みのストレージクラスが付属していません。 ローカルストレージまたは[ルーク](https://github.com/rook/rook)などの優先プロビジョナーを使用して、独自のストレージクラスと永続ボリュームを作成する必要があります。 その場合は、構成したストレージクラスに**className**を設定します。 

> [!NOTE]
>  *Kubeadm kubeadm*の組み込みの配置構成ファイルでは、データとログストレージにストレージクラス名が指定されていません。 デプロイする前に、構成ファイルをカスタマイズして className の値を設定する必要があります。そうしないと、配置前検証は失敗します。 また、デプロイには、ストレージクラスが存在するかどうかを確認する検証手順もありますが、必要な永続ボリュームには含まれません。 クラスターのスケールに応じて、十分な量のボリュームを作成しておく必要があります。 CTP 3.1 では、既定のクラスターサイズとして、少なくとも23個のボリュームを作成する必要があります。 ローカルプロビジョナーを使用して永続ボリュームを作成する方法の例を[次](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu)に示します。


## <a name="customize-storage-configurations-for-each-pool"></a>各プールのストレージ構成をカスタマイズする

すべてのカスタマイズでは、最初に、使用する組み込み構成ファイルのコピーを作成する必要があります。 たとえば、次のコマンドは、 *aks*展開構成ファイルのコピーをという名前`custom`のサブディレクトリに作成します。

```bash
azdata bdc config init --source aks-dev-test --target custom
```

これにより、**クラスター**を手動で編集するか、 **azdata bdc config**コマンドを使用することによってカスタマイズできる2つのファイルが作成されます。 Jsonpath と jsonpath ライブラリの組み合わせを使用して、構成ファイルを編集する方法を提供できます。


### <a id="config-samples"></a>ストレージクラス名と要求サイズのいずれかまたは両方を構成します

既定では、クラスターでプロビジョニングされた各ポッドに対してプロビジョニングされた永続的なボリューム要求のサイズは 10 GB です。 この値は、クラスターの展開前にカスタム構成ファイルで実行しているワークロードに合わせて更新できます。

次の例では、永続的なボリューム要求サイズのサイズを、コントロールの32Gi に更新し**ます。 jsaon**。 プールレベルで上書きされない場合、この設定はすべてのプールに適用されます。

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.storage.data.size=100Gi"
```

次の例は、**コントロールの json**ファイルのストレージクラスを変更する方法を示しています。

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.storage.data.className=<yourStorageClassName>"
```

別の方法として、カスタム構成ファイルを手動で編集するか、次の例のように、記憶域プールのストレージクラスを変更する json パッチを使用することもできます。 次の内容を含む*patch. json*ファイルを作成します。

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec.storage"
      "value": {
          "type":"Storage",
          "replicas":2,
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

修正プログラムファイルを適用します。 **Azdata bdc の構成パッチ**コマンドを使用して、JSON 修正プログラムファイルに変更を適用します。 次の例では、修正プログラムの json ファイルを、ターゲットの配置構成ファイルのカスタム json に適用します。

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a name="next-steps"></a>次の手順

Kubernetes のボリュームに関する詳細なドキュメントについては、[ボリュームに関する Kubernetes のドキュメント](https://kubernetes.io/docs/concepts/storage/volumes/)を参照してください。

SQL Server ビッグデータクラスターのデプロイの詳細については、「 [Kubernetes で SQL Server ビッグデータクラスターをデプロイする方法](deployment-guidance.md)」を参照してください。

