---
title: bash スクリプトを使用して単一ノード kubeadm クラスターに展開する
titleSuffix: SQL Server big data clusters
description: bash 展開スクリプトを使用して、SQL Server 2019 ビッグ データ クラスター (プレビュー) を単一ノード kubeadm クラスターに展開します。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 37017221b636146a003f8af8890c655ed605bca9
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68473074"
---
# <a name="deploy-with-a-bash-script-to-a-single-node-kubeadm-cluster"></a>bash スクリプトを使用して単一ノード kubeadm クラスターに展開する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このチュートリアルでは、サンプルの bash 展開スクリプトを利用し、kubeadm と SQL Server ビッグ データ クラスターを使用して単一ノード Kubernetes クラスターを展開します。  

## <a name="prerequisites"></a>Prerequisites

- バニラ Ubuntu 18.04 または 16.04 **サーバー**の VM。 スクリプトによってすべての依存関係が設定され、VM 内からそのスクリプトを実行します。

  > [!NOTE]
  > Azure VM の使用は、まだサポートされていません。

- VM には、少なくとも 8 個の CPU、64 GB の RAM、および 100 GB のディスク領域が必要です。 すべてのビッグ データ クラスターの Docker イメージをプルした後は、すべてのコンポーネント全体で使用するデータとログに対して 50 GB が残されます。

## <a name="instructions"></a>Instructions

1. 展開に使用することを計画している VM 上にスクリプトをダウンロードします。

   ```bash
   curl --output setup-bdc.sh https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/setup-bdc.sh
   ```

2. 次のコマンドを使用して、スクリプトを実行可能にします。

   ```bash
   chmod +x setup-bdc.sh
   ```

3. **sudo** を使用してスクリプトを実行します。

   ```bash
   sudo ./setup-bdc.sh
   ```

   要求された場合は、次の外部エンドポイント、つまり、コントローラー、SQL Server マスター、ゲートウェイに使用するパスワードの入力値を指定します。 コントローラーのユーザー名の既定値は、*admin* です。

4. **azdata** ツールに対して別名を設定します。

   ```bash
   source ~/.bashrc
   ```

5. 別名が機能することを確認します。

   ```bash
   azdata --version
   ```

## <a name="next-steps"></a>次の手順

ビッグ データ クラスターの使用を開始するには、[こちらのチュートリアル](tutorial-load-sample-data.md)に従ってください。
