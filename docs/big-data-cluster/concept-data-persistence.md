---
title: Kubernetes クラスターのビッグ データ、SQL Server でのデータ永続化 |Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 629d7fd887e96013b17a5686ce82eb966044f240
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796649"
---
# <a name="data-persistence-with-sql-server-big-data-cluster-on-kubernetes"></a>Kubernetes 上の SQL Server のビッグ データ クラスターでのデータ永続化

[永続ボリューム](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)の消費用途から抽象化された記憶域の提供を Kubernetes での記憶域が完了したは、プラグイン モデルを提供します。 そのため、独自の高可用性記憶域を移動し、SQL Server のビッグ データ クラスターに接続できます。 これにより、ストレージ、可用性、および必要なパフォーマンスの種類を完全に制御できるようにします。 Kubernetes では、さまざまな種類の Azure ディスク/ファイル、NFS、ローカルのストレージなどの記憶域ソリューションをサポートします。

## <a name="configure-persistent-volumes"></a>永続ボリュームを構成します。

使用してビッグ データの SQL Server クラスターは、これらの永続的なボリュームを使用する方法は、[ストレージ クラス](https://kubernetes.io/docs/concepts/storage/storage-classes/)します。 異なる種類のストレージ用のさまざまなストレージ クラスを作成し、ビッグ データ クラスターのデプロイ時にそれらを指定できます。 目的 (プール) を使用するには、どのストレージ クラスを構成することができます。 SQL Server のビッグ データ クラスターを作成します[永続ボリューム要求](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims)永続ボリュームが必要なポッドごとの指定した記憶域クラス名を指定します。 ポッドに対応する永続的なボリュームをマウントします。

> [!NOTE]
> CTP 2.0 でのみ`ReadWriteOnce`クラスター全体のアクセス モードがサポートされています。

## <a name="deployment-settings"></a>展開の設定

永続的なストレージを使用するには、デプロイ時に構成する、 **USE_PERSISTENT_VOLUME**と**STORAGE_CLASS_NAME**実行する前に環境変数`mssqlctl create cluster`コマンド。 **USE_PERSISTENT_VOLUME**に設定されている`true`既定。 既定値をオーバーライドしてに設定`false`と、ここでは、SQL Server のビッグ データ クラスターが emptyDir マウントを使用します。 

> [!WARNING]
> 非機能的なクラスターは、永続的な記憶域のない実行中の可能性があります。 ポッドが再起動するとクラスター メタデータ、またはユーザー データは完全に失われます。

指定する必要があるフラグを true に設定した場合**STORAGE_CLASS_NAME**デプロイ時にパラメーターとして。

## <a name="aks-storage-classes"></a>AKS のストレージ クラス

AKS が付属して[2 つの組み込みストレージ クラス](https://docs.microsoft.com/en-us/azure/aks/azure-disks-dynamic-pv)**既定**と**premium ストレージ**に動的プロビジョナーと共にします。 これらのいずれかを指定するか、永続的なストレージが有効になっているとビッグ データ クラスターをデプロイするため、独自のストレージ クラスを作成します。

## <a name="minikube-storage-class"></a>Minikube ストレージ クラス

呼ばれる組み込みストレージ クラスが付属して Minikube**標準**その動的プロビジョナーと共にします。

## <a name="kubeadm"></a>Kubeadm

Kubeadm が組み込みストレージ クラスが付属していません永続ボリュームとストレージ クラスのローカル ストレージを使用して設定するスクリプトを作成したため、または[ルーク](https://github.com/rook/rook)ストレージ。

## <a name="on-premises-cluster"></a>オンプレミス クラスター

オンプレミス クラスター明らかに付属していない任意の組み込みストレージ クラス、したがってを設定する必要があります[永続ボリューム](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)/[プロビジョナー](https://kubernetes.io/docs/concepts/storage/dynamic-provisioning/)事前し、対応するを使用してSQL Server のビッグ データ クラスターのデプロイ時にストレージ クラスです。

# <a name="customize-storage-size-for-each-pool"></a>各プールの記憶域のサイズをカスタマイズします。
既定では、各クラスターのプロビジョニングのポッドのプロビジョニングされた永続的なボリュームのサイズは 6 GB です。 これは、環境変数を設定して構成可能な`STORAGE_SIZE`を別の値。 たとえば、次のコマンドを実行する前に 10 GB に値を設定する実行することができます、`mssqlctl create cluster command`します。

```bash
export STORAGE_SIZE=10Gi
```

永続的な記憶域の設定ごとに異なる構成は、このようなストレージ クラスの名前と、クラスター内の異なるプール用の永続的なボリューム サイズすることもできます。 たとえば、クラスターをデプロイする前に環境変数の下の設定によって異なるストレージ クラスを使用し、容量の増加する記憶域プールのデプロイされた永続ボリュームを構成できます。

```bash
export STORAGE_POOL_USE_PERSISTENT_VOLUME=true
export STORAGE_POOL_STORAGE_CLASS_NAME=premium-storage
export STORAGE_POOL_STORAGE_SIZE=100Gi
```

SQL Server のビッグ データ クラスターの永続的なストレージのセットアップに関連する環境変数の包括的な一覧を次に示します。

| 環境変数 | 既定値 | 説明 |
|---|---|---|
| **USE_PERSISTENT_VOLUME** | true | `true` Kubernetes 永続ボリュームを使用するには、ポッドの記憶域を要求します。 `false` ポッドの記憶域の一時的なホストの記憶域を使用します。 |
| **STORAGE_CLASS_NAME** | 既定値 (default) | 場合`USE_PERSISTENT_VOLUME`は`true`を使用する Kubernetes ストレージ クラスの名前を示します。 |
| **STORAGE_SIZE** | 6 gi | 場合`USE_PERSISTENT_VOLUME`は`true`、ポッドごとの永続ボリュームのサイズを示します。 |
| **DATA_POOL_USE_PERSISTENT_VOLUME** | USE_PERSISTENT_VOLUME | `true` Kubernetes 永続ボリュームを使用するには、データ プール内のポッドを要求します。 `false` データ プール ポッドの一時的なホストの記憶域を使用します。 |
| **DATA_POOL_STORAGE_CLASS_NAME** | STORAGE_CLASS_NAME | プールのポッドをデータに関連付けられた永続的なボリュームを使用する Kubernetes ストレージ クラスの名前を示します。|
| **DATA_POOL_STORAGE_SIZE** | STORAGE_SIZE |データのプール内の各ポッドの永続ボリュームのサイズを示します。 |
| **STORAGE_POOL_USE_PERSISTENT_VOLUME** | USE_PERSISTENT_VOLUME | `true` Kubernetes 永続ボリュームを使用するには、記憶域プール内のポッドを要求します。 `false` 記憶域プールのポッドの一時的なホストの記憶域を使用します。|
| **STORAGE_POOL_STORAGE_CLASS_NAME** | STORAGE_CLASS_NAME | TIndicates 記憶域プールのポッドに関連付けられた永続的なボリュームを使用する Kubernetes ストレージ クラスの名前。 |
| **STORAGE_POOL_STORAGE_SIZE** | STORAGE_SIZE | 記憶域プール内の各ポッドの永続ボリュームのサイズを示します。 |

## <a name="next-steps"></a>次の手順

Kubernetes でのボリュームに関する詳細なドキュメントを参照してください、[ボリューム上の Kubernetes のドキュメント](https://kubernetes.io/docs/concepts/storage/volumes/)します。

SQL Server のビッグ データ クラスターのデプロイの詳細については、次を参照してください。[を Kubernetes クラスターのビッグ データ、SQL Server をデプロイする方法](deployment-guidance.md)します。

