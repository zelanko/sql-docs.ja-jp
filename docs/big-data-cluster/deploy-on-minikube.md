---
title: Minikube を SQL Server 2019 CTP 2.0 の展開の構成 |Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 1f20f2adc916a456e4a1975804fac1640ee95f69
ms.sourcegitcommit: 8aecafdaaee615b4cd0a9889f5721b1c7b13e160
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2018
ms.locfileid: "48818050"
---
# <a name="configure-minikube-for-sql-server-2019-ctp-20"></a>Minikube を SQL Server 2019 CTP 2.0 を構成します。

Minikube は、ラップトップやデスクトップなどの単一のコンピューター上で Kubernetes を実行しやすくツールです。 Minikube は実行 Kubernetes を試すか、それを使用した開発を検討しているユーザーのラップトップ コンピューターで、VM 内で単一ノードの Kubernetes クラスターを日常的なされます。 

## <a name="prerequisites"></a>前提条件

- SQL のビッグ データ クラスター構成では、SQL Server 2019 CTP 2.0 Minikube クラスターを実行するには、コンピューターに少なくとも 32 GB の RAM があることをお勧めします。

   > [!TIP] 
   > コンピューターに十分なメモリがある場合は、クラスター構成するように変更数が 3 つのインスタンスが作成されます: 1 つのマスター インスタンスと 2 つのコンピューティング インスタンス。

- -X VT または amd-v の仮想化は、コンピューターの BIOS で有効にする必要があります。

## <a name="install-dependencies"></a>依存関係をインストールします。

1. インストールされていない場合は、ローカルに git をインストール[Windows](https://git-for-windows.github.io/)、 [、Linux または Mac](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)します。

1. インストール[kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)します。

1. Python 3 をインストールします。
   - Pip が不足している場合は、ダウンロード[get clspip.py](https://bootstrap.pypa.io/get-pip.py)実行`python get-pip.py`します。
   - インストール要求を使用してパッケージ`python -m pip install requests`します。

1. インストールされているハイパーバイザーがいない場合は、今すぐインストールします。
   - OS X、インストール[xhyve ドライバー](https://git.k8s.io/minikube/docs/drivers.md)、 [VirtualBox](https://www.virtualbox.org/wiki/Downloads)、または[VMware Fusion](https://www.vmware.com/products/fusion)します。
   - Linux の場合は、インストール[VirtualBox](https://www.virtualbox.org/wiki/Downloads)または[KVM](http://www.linux-kvm.org/)します。
   - Windows では、インストール[VirtualBox](https://www.virtualbox.org/wiki/Downloads)または[HYPER-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install)します。 Hyper-v で構成されている外部スイッチがいない場合は、外部のネットワーク アクセス権を持つ 1 つを作成します。  表示する方法[minikube の hyper-v で外部スイッチを作成](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/)です。

## <a name="install-minikube"></a>Minikube をインストールします。

Minikube をインストールするための手順に従って、 [v0.28.2 リリース](https://github.com/kubernetes/minikube/releases/tag/v0.28.2)します。 SQL Server 2019 CTP 2.0 のビッグ データ クラスターは、バージョン v0.24.1 と構成にのみ機能します。

## <a name="create-a-minikube-cluster"></a>Minikube クラスターを作成します。

次のコマンドでは、8 個の Cpu を使用して、HYPER-V VM、28 GB のメモリ、および 100 GB のディスクのサイズに minikube クラスターを作成します。 ディスクのサイズは、予約済みの領域でがありません。  それはディスクにそのサイズを拡大に応じてがします。  ディスクを変更しないことをお勧めします。 このテストでの問題に直面したのと、100 GB 未満を何かする領域。 これも hyper-v スイッチ外部アクセス権を持つ明示的に指定します。

パラメーターを変更します。 **--メモリ**によっては、使用可能なハードウェアと必要に応じて、ハイパーバイザーを使用しています。  確認、 **--hyper v**仮想スイッチのパラメーターの値が、仮想スイッチを作成するときに使用した名前と一致します。

```bash
minikube start --vm-driver="hyperv" --cpus 8 --memory 28672 --disk-size 100g --hyperv-virtual-switch "External"
```

VirtualBox を使用した、Minikube を使用している場合、コマンドは次のようになります。

```base
minikube start --cpus 8 --memory 28672 --disk-size 100g
```

## <a name="disable-automatic-checkpoint-with-hyper-v"></a>Hyper-v を使用した自動チェックポイントを無効にします。

Windows 10 では、自動チェックポイントは、VM で有効にします。 VM での自動チェックポイントを無効にする PowerShell で次のコマンドを実行します。

```PowerShell
Set-VM -Name minikube -CheckpointType Disabled -AutomaticCheckpointsEnabled $false
```

## <a name="next-steps"></a>次の手順

この記事の手順では、Minikube クラスターを構成します。 次の手順では、クラスターに SQL Server 2019 CTP 2.0 を展開します。

[SQL Server 2019 CTP 2.0 では、Kubernetes をデプロイします。](deployment-guidance.md#deploy)
