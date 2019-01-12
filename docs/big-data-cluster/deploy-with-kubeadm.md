---
title: Kubeadm で Kubernetes を構成します。
titleSuffix: SQL Server 2019 big data clusters
description: 複数の Ubuntu 16.04 上の Kubernetes または 18.04 のマシン (物理または仮想) の SQL Server 2019 ビッグ データ クラスター (プレビュー) のデプロイを構成する方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 78d2024f09e78645d8fa1c35279b296e3cda53d7
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241593"
---
# <a name="configure-kubernetes-on-multiple-machines-for-sql-server-2019-big-data-cluster-preview-deployments"></a>複数のコンピューターの SQL Server 2019 ビッグ データ クラスター (プレビュー) のデプロイでの Kubernetes を構成します。

この記事では、使用する方法の例を示します**kubeadm**を複数のコンピューターの SQL Server 2019 ビッグ データ クラスター (プレビュー) のデプロイで Kubernetes を構成します。 この例では、複数の Ubuntu 16.04 または 18.04 LTS マシン (物理または仮想)、ターゲットとは。 さまざまな Linux プラットフォームに展開する場合、システムに一致するようにコマンドの一部を変更する必要があります。  

> [!TIP] 
> Kubernetes を構成するサンプル スクリプトでは、次を参照してください。 [Kubeadm を Ubuntu 16.04 LTS または 18.04 LTS を使用して Kubernetes クラスターを作成する](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm)します。

## <a name="prerequisites"></a>前提条件

- 複数の Linux の物理マシンまたは仮想マシン、クラスターで使用するには
- 推奨される構成:8 個の Cpu、32 GB のメモリ、および各マシンの記憶域の 100 GB 以上
- クラスター内の 3 つのマシンの最小値

## <a name="prepare-the-machines"></a>マシンを準備します。

各コンピューターでは、いくつか必要な前提条件があります。 Bash 端末では、各コンピューターで、次のコマンドを実行します。

1. 現在のマシンを追加、`/etc/hosts`ファイル。

   ```bash
   echo $(hostname -i) $(hostname) | sudo tee -a /etc/hosts
   ```

1. すべてのデバイスでのスワップを無効にします。

   ```bash
   sudo sed -i "/ swap / s/^/#/" /etc/fstab
   sudo swapoff -a
   ```

1. キーをインポートし、Kubernetes のリポジトリを登録します。

   ```bash
   sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
   echo 'deb http://apt.kubernetes.io/ kubernetes-xenial main' | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
   ```

1. マシンに docker と Kubernetes の前提条件を構成します。

   ```bash
   KUBE_DPKG_VERSION=1.11.3-00
   sudo apt-get update && /
   sudo apt-get install -y ebtables ethtool && /
   sudo apt-get install -y docker.io && /
   sudo apt-get install -y apt-transport-https && /
   sudo apt-get install -y kubelet=$KUBE_DPKG_VERSION kubeadm=$KUBE_DPKG_VERSION kubectl=$KUBE_DPKG_VERSION && /
   curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
   ```
 
1. `net.bridge.bridge-nf-call-iptables=1` を設定します。 Ubuntu の 18.04 で、次のコマンドが最初に有効に`br_netfilter`します。

   ```bash
   . /etc/os-release
   if [ "$VERSION_CODENAME" == "bionic" ]; then sudo modprobe br_netfilter; fi
   sudo sysctl net.bridge.bridge-nf-call-iptables=1
   ```

## <a name="configure-the-kubernetes-master"></a>Kubernetes マスターを構成します。

各コンピューターで、前のコマンドを実行した後、Kubernetes マスターとして指定する、マシンのいずれかを選択します。 そのコンピューターで、次のコマンドを楽しいします。

1. 最初に、次のコマンドを使用して、現在のディレクトリに rbac.yaml ファイルを作成します。 

   ```bash
   cat <<EOF > rbac.yaml
   apiVersion: rbac.authorization.k8s.io/v1beta1
   kind: ClusterRoleBinding
   metadata:
     name: default-rbac
   subjects:
   - kind: ServiceAccount
     name: default
     namespace: default
   roleRef:
     kind: ClusterRole
     name: cluster-admin
     apiGroup: rbac.authorization.k8s.io
   EOF
   ```

1. このコンピューター上の Kubernetes マスターを初期化します。 Kubernetes マスターが正常に初期化する出力が表示されます。

   ```bash
   KUBE_VERSION=1.11.3
   sudo kubeadm init --pod-network-cidr=10.244.0.0/16 --kubernetes-version=$KUBE_VERSION
   ```

1. 注、`kubeadm join`コマンドを他のサーバーを使用して Kubernetes クラスターに参加する必要があります。 後で使用できるは、これをコピーします。

   ![kubeadm 結合](./media/deploy-with-kubeadm/kubeadm-join.png)

1. Kubernetes 構成ファイルをホーム ディレクトリを設定します。

   ```bash
   mkdir -p $HOME/.kube
   sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
   sudo chown $(id -u):$(id -g) $HOME/.kube/config
   ```

1. クラスターと、Kubernetes ダッシュ ボードを構成します。

   ```bash
   kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
   helm init
   kubectl apply -f rbac.yaml
   kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
   kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
   ```

## <a name="configure-the-kubernetes-agents"></a>Kubernetes エージェントを構成します。

その他のマシンは、Kubernetes クラスターのエージェントとして機能します。 

その他のマシンごとに実行、`kubeadm join`前のセクションでコピーしたコマンド。

![kubeadm 結合エージェント](./media/deploy-with-kubeadm/kubeadm-join-agents.png)

## <a name="view-the-cluster-status"></a>クラスターの状態を表示します。

クラスターへの接続を確認するため、 [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)コマンドをクラスター ノードの一覧を返します。

```bash
kubectl get nodes
```

## <a name="next-steps"></a>次の手順

この記事の手順では、複数の Ubuntu コンピューターで Kubernetes クラスターを構成します。 次の手順では、SQL Server 2019 ビッグ データのクラスターにデプロイします。 手順については、次の記事を参照してください。

[SQL Server 2019 CTP 2.2 を Kubernetes をデプロイします。](deployment-guidance.md#deploy)
