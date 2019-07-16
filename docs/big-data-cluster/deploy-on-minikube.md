---
title: Minikube を構成します。
titleSuffix: SQL Server big data clusters
description: 1 台のコンピューターでのビッグ データ クラスター (プレビュー) のデプロイを SQL Server 2019 minikube を構成する方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6c2261b5cfbbe590c76ce410da4b95ee678a20b5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958474"
---
# <a name="configure-minikube-for-sql-server-big-data-cluster-deployments"></a>SQL Server のビッグ データ クラスター展開 minikube を構成します。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、構成する方法を説明**minikube**単一のコンピューターの SQL Server 2019 ビッグ データ クラスター (プレビュー) のデプロイにします。 Minikube は、ラップトップやデスクトップなどの単一のコンピューター上で Kubernetes を実行しやすくツールです。 Minikube は実行 Kubernetes を試すか、それを使用した開発を検討しているユーザーのラップトップ コンピューターで、VM 内で単一ノードの Kubernetes クラスターを日常的なされます。 

## <a name="prerequisites"></a>必須コンポーネント

- 32 GB のメモリ (64 GB を推奨)。

- コンピューターに推奨されるメモリの最小値のみがある場合は、プールのコンピューティング インスタンスの 1 つだけ、1 つのデータ プール インスタンスと 1 の記憶域プールのインスタンスがクラスターのデプロイを構成します。 この構成のみ使用してください評価環境の持続性とデータの可用性が重要です。 参照してください、[のデプロイに関するドキュメント](deployment-guidance.md#configfile)データ プールのレプリカの数を構成する設定を環境変数の詳細については、プール、および記憶域プールを計算します。

- -X VT または amd-v の仮想化は、コンピューターの BIOS で有効にする必要があります。

## <a name="install-dependencies"></a>依存関係をインストールします。

1. インストール[kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)します。

1. Python 3 をインストールします。
   - Pip が不足している場合は、ダウンロード[get clspip.py](https://bootstrap.pypa.io/get-pip.py)実行`python get-pip.py`します。
   - インストール要求を使用してパッケージ`python -m pip install requests`します。

1. インストールされているハイパーバイザーがいない場合は、今すぐインストールします。
   - OS X、インストール[xhyve ドライバー](https://git.k8s.io/minikube/docs/drivers.md)、 [VirtualBox](https://www.virtualbox.org/wiki/Downloads)、または[VMware Fusion](https://www.vmware.com/products/fusion)します。
   - Linux の場合は、インストール[VirtualBox](https://www.virtualbox.org/wiki/Downloads)または[KVM](https://www.linux-kvm.org/)します。
   - Windows では、インストール[VirtualBox](https://www.virtualbox.org/wiki/Downloads)または[HYPER-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install)します。 Hyper-v で構成されている外部スイッチがいない場合は、外部のネットワーク アクセス権を持つ 1 つを作成します。  表示する方法[minikube の hyper-v で外部スイッチを作成](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/)です。

## <a name="install-minikube"></a>Minikube をインストールします。

インストールの指示に従って minikube、 [v0.28.2 リリース](https://github.com/kubernetes/minikube/releases/tag/v0.28.2)します。 SQL Server 2019 ビッグ データ クラスター (プレビュー) は、バージョン v0.24.1 と構成にのみ機能します。

## <a name="create-a-minikube-cluster"></a>Minikube クラスターを作成します。

次のコマンドでは、8 個の Cpu を使用して、HYPER-V VM、28 GB のメモリ、および 100 GB のディスクのサイズに minikube クラスターを作成します。 ディスクのサイズは、予約済みの領域でがありません。  それはディスクにそのサイズを拡大に応じてがします。  ディスクを変更しないことをお勧めします。 このテストでの問題に直面したのと、100 GB 未満を何かする領域。 これも hyper-v スイッチ外部アクセス権を持つ明示的に指定します。

パラメーターを変更します。 **--メモリ**によっては、使用可能なハードウェアと必要に応じて、ハイパーバイザーを使用しています。  確認、 **--hyper v**仮想スイッチのパラメーターの値が、仮想スイッチを作成するときに使用した名前と一致します。

```bash
minikube start --vm-driver="hyperv" --cpus 8 --memory 28672 --disk-size 100g --hyperv-virtual-switch "External"
```

VirtualBox を使用した、minikube を使用している場合、コマンドは次のようになります。

```base
minikube start --cpus 8 --memory 28672 --disk-size 100g
```

## <a name="disable-automatic-checkpoint-with-hyper-v"></a>Hyper-v を使用した自動チェックポイントを無効にします。

Windows 10 では、自動チェックポイントは、VM で有効にします。 VM での自動チェックポイントを無効にする PowerShell で次のコマンドを実行します。

```PowerShell
Set-VM -Name minikube -CheckpointType Disabled -AutomaticCheckpointsEnabled $false
```

## <a name="next-steps"></a>次の手順

この記事の手順では、minikube クラスターを構成します。 次の手順では、SQL Server 2019 ビッグ データのクラスターにデプロイします。 手順については、次の記事を参照してください。

[Kubernetes での SQL Server 2019 ビッグ データ クラスターを展開します。](deployment-guidance.md#deploy)
