---
title: Kubeadm を使用して Kubernetes を構成する
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグデータクラスター (プレビュー) のデプロイのために、複数の Ubuntu 16.04 または18.04 マシン (物理または仮想) で Kubernetes を構成する方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ea79503869e7d403e4d3f4f960de9c95760eda0f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419444"
---
# <a name="configure-kubernetes-on-multiple-machines-for-sql-server-big-data-cluster-deployments"></a>SQL Server ビッグデータクラスターの展開のために複数のマシンで Kubernetes を構成する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、 **kubeadm**を使用して、SQL Server 2019 ビッグデータクラスター (プレビュー) のデプロイ用に複数のコンピューターで Kubernetes を構成する方法の例を示します。 この例では、複数の Ubuntu 16.04 または 18.04 LTS マシン (物理または仮想) がターゲットです。 別の Linux プラットフォームにデプロイする場合は、システムに合わせていくつかのコマンドを変更する必要があります。  

> [!TIP] 
> Kubernetes を構成するサンプルスクリプトについては、「 [Ubuntu 16.04 LTS または 18.04 LTS で Kubeadm を使用して Kubernetes クラスターを作成](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm)する」を参照してください。

## <a name="prerequisites"></a>前提条件

- 最低3台の Linux 物理マシンまたは仮想マシン
- コンピューターごとの推奨構成:
   - 8 Cpu
   - 64 GB のメモリ
   - 100 GB のストレージ

## <a name="prepare-the-machines"></a>マシンを準備する

各コンピューターには、いくつかの必須の前提条件があります。 Bash ターミナルで、各コンピューターで次のコマンドを実行します。

1. 現在のコンピューターを`/etc/hosts`ファイルに追加します。

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

1. コンピューターで docker と Kubernetes の前提条件を構成します。

   ```bash
   KUBE_DPKG_VERSION=1.11.3-00
   sudo apt-get update && /
   sudo apt-get install -y ebtables ethtool && /
   sudo apt-get install -y docker.io && /
   sudo apt-get install -y apt-transport-https && /
   sudo apt-get install -y kubelet=$KUBE_DPKG_VERSION kubeadm=$KUBE_DPKG_VERSION kubectl=$KUBE_DPKG_VERSION && /
   curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
   ```
 
1. `net.bridge.bridge-nf-call-iptables=1` を設定します。 Ubuntu 18.04 では、次のコマンドで`br_netfilter`最初にを有効にします。

   ```bash
   . /etc/os-release
   if [ "$VERSION_CODENAME" == "bionic" ]; then sudo modprobe br_netfilter; fi
   sudo sysctl net.bridge.bridge-nf-call-iptables=1
   ```

## <a name="configure-the-kubernetes-master"></a>Kubernetes マスターの構成

各コンピューターで上記のコマンドを実行した後、Kubernetes マスターにするコンピューターのいずれかを選択します。 その後、そのコンピューターで次のコマンドを実行します。

1. まず、次のコマンドを使用して、現在のディレクトリに rbac. yaml ファイルを作成します。 

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

1. このコンピューターの Kubernetes マスターを初期化します。 Kubernetes マスターが正常に初期化されたことを示す出力が表示されます。

   ```bash
   KUBE_VERSION=1.11.3
   sudo kubeadm init --pod-network-cidr=10.244.0.0/16 --kubernetes-version=$KUBE_VERSION
   ```

1. Kubernetes クラスター `kubeadm join`に参加するために、他のサーバーで使用する必要があるコマンドに注意してください。 後で使用するためにこれをコピーします。

   ![kubeadm join](./media/deploy-with-kubeadm/kubeadm-join.png)

1. Kubernetes 構成ファイルにホームディレクトリを設定します。

   ```bash
   mkdir -p $HOME/.kube
   sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
   sudo chown $(id -u):$(id -g) $HOME/.kube/config
   ```

1. クラスターと Kubernetes ダッシュボードを構成します。

   ```bash
   kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
   helm init
   kubectl apply -f rbac.yaml
   kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
   kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
   ```

## <a name="configure-the-kubernetes-agents"></a>Kubernetes エージェントを構成する

他のマシンは、クラスター内の Kubernetes エージェントとして機能します。 

他の各コンピューターで、前のセクション`kubeadm join`でコピーしたコマンドを実行します。

![kubeadm 参加エージェント](./media/deploy-with-kubeadm/kubeadm-join-agents.png)

## <a name="view-the-cluster-status"></a>クラスターの状態を表示する

クラスターへの接続を確認するには、 [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)コマンドを使用してクラスターノードの一覧を返します。

```bash
kubectl get nodes
```

## <a name="next-steps"></a>次のステップ

この記事の手順では、複数の Ubuntu コンピューターで Kubernetes クラスターを構成しました。 次の手順では、SQL Server 2019 ビッグデータクラスターをデプロイします。 手順については、次の記事を参照してください。

[Kubernetes に SQL Server をデプロイする](deployment-guidance.md#deploy)
