---
title: Minikube を構成する
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグ データ クラスター (プレビュー) の展開のために、単一マシンで minikube を構成する方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1991176de132062c46f36f30f4f384e483c069f9
ms.sourcegitcommit: 316c25fe7465b35884f72928e91c11eea69984d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68969414"
---
# <a name="configure-minikube-for-sql-server-big-data-cluster-deployments"></a>SQL Server ビッグ データ クラスターの展開のために minikube を構成する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) の展開のために、単一マシンで **minikube** を構成する方法について説明します。 Minikube は、ラップトップやデスクトップなどの単一のコンピューターで Kubernetes を簡単に実行できるツールです。 Minikube では、Kubernetes を試したり、日常的に開発したりしようとしているユーザーのために、ラップトップの VM 内で単一ノードの Kubernetes クラスターが実行されています。 

## <a name="prerequisites"></a>必須コンポーネント

- 64 GB のメモリ。

- コンピューターに最小推奨メモリしかない場合は、1 つのコンピューティング プール インスタンス、1 つのデータ プール インスタンス、および 1 つの記憶域プール インスタンスだけを持つようにクラスターの展開を構成します。 この構成は、データの持続性と可用性が重要ではない評価環境に対してのみ使用してください。 データ プール、コンピューティング プール、記憶域プールのレプリカの数を構成するために設定する環境変数の詳細については、[展開のドキュメント](deployment-guidance.md#configfile)を参照してください。

- コンピューターの BIOS で VT-x または AMD-v の仮想化を有効にする必要があります。

## <a name="install-dependencies"></a>依存関係のインストール

1. [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) をインストールします。

1. ハイパーバイザーがまだインストールされていない場合は、今すぐインストールしてください。
   - OS X の場合は、[xhyve driver](https://git.k8s.io/minikube/docs/drivers.md)、[VirtualBox](https://www.virtualbox.org/wiki/Downloads)、または [VMware Fusion](https://www.vmware.com/products/fusion) をインストールします。
   - Linux の場合は、[VirtualBox](https://www.virtualbox.org/wiki/Downloads) または [KVM](https://www.linux-kvm.org/) をインストールします。
   - Windows の場合は、[VirtualBox](https://www.virtualbox.org/wiki/Downloads) または [Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install) をインストールします。 Hyper-v で外部スイッチが構成されていない場合は、外部ネットワークアクセスを持つものを作成します。 [Minikube の hyper-v で外部スイッチを作成](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/)する方法について説明します。

## <a name="install-minikube"></a>Minikube のインストール

Minikube リリースは、 [v 1.3.0 リリース](https://github.com/kubernetes/minikube/releases/tag/v1.3.0)の手順に従ってインストールしてください。 SQL Server 2019 ビッグデータクラスター (プレビュー) は、バージョン1.0.0 以降でのみ動作します。

## <a name="create-a-minikube-cluster"></a>Minikube クラスターの作成

次のコマンドは、8個の Cpu、64 GB のメモリ、および 100 GB のディスクサイズを使用して、Hyper-v VM に minikube クラスターを作成します。 ディスク サイズは予約領域ではありません。  必要に応じて、ディスク上のサイズに拡大します。  テストで問題が発生したため、ディスク領域を 100 GB 未満に変更しないことをお勧めします。 これは、外部アクセスが明示的に指定された Hyper-v スイッチも指定します。

使用するハードウェアや、どのハイパーバイザーを使用しているかに応じて、 **--memory** などのパラメーターを変更します。  **--hyper-v** 仮想スイッチ パラメーターの値が、仮想スイッチの作成時に使用した名前と一致していることを確認します。

```bash
minikube start --vm-driver="hyperv" --cpus 8 --memory 65536 --disk-size 100g --hyperv-virtual-switch "External"
```

VirtualBox で minikube を使用している場合、コマンドは次のようになります。

```base
minikube start --cpus 8 --memory 65536 --disk-size 100g
```

## <a name="disable-automatic-checkpoint-with-hyper-v"></a>Hyper-V で自動チェックポイントを無効にする

Windows 10 では、VM で自動チェックポイントが有効になっています。 PowerShell で次のコマンドを実行して、VM で自動チェックポイントを無効にし、メモリを静的に設定します。

```PowerShell
Set-VM -Name minikube -CheckpointType Disabled -AutomaticCheckpointsEnabled $false -StaticMemory
```

## <a name="next-steps"></a>次の手順

この記事の手順では、クラスターに minikube クラスターを構成しました。 次のステップとして、SQL Server 2019 ビッグ データ クラスターを展開します。 手順については、次の記事を参照してください。

[Kubernetes 上に SQL Server 2019 ビッグ データ クラスターを展開する](deployment-guidance.md#deploy)
