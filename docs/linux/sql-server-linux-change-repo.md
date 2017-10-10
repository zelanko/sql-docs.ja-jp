---
title: "登録、SQL Server on Linux の一般提供リポジトリ |Microsoft ドキュメント"
description: "Linux 上の一般公開 (GA) リポジトリにプレビュー SQL Server 2017 リポジトリからリポジトリを変更 (GA もとも呼ば RTM)。"
author: annashres
ms.author: anshrest
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: a0d6ff0a983f1d1d1ad8fdcc7de37d9a06032025
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="change-repositories-from-the-preview-repository-to-the-ga-repository"></a>リポジトリをプレビュー リポジトリから GA リポジトリに変更します。

SQL Server 2017 を CTP 2.1、RC1、または RC2 から一般公開 (GA) リリースにアップグレードするときに、リポジトリにする必要があります。 次のセクションでは、任意のリポジトリとアップグレードする前に変更を行う方法を説明します。

## <a name="repository-choices"></a>リポジトリの選択

ことが重要の各配布リポジトリの 2 つの主な種類があることに注意してください。

  > [!IMPORTANT]
  > GA. にアップグレードする前に 2.1 には、少なくともに CTP 2.1 より前の任意のバージョンをアップグレードする必要があります。

- **累積的な更新プログラム (CU)**:、累積的な更新プログラム (CU) リポジトリには、そのリリース以降、基本の SQL Server リリースおよびバグの修正や改善用のパッケージが含まれます。 累積的更新プログラムは、SQL Server 2017 などのリリース バージョンに固有です。 正規わかりませんがリリースされます。

- **GDR**: の GDR リポジトリには、そのリリース以降、基本の SQL Server リリースのみ重要な修正プログラムとセキュリティ更新プログラム用のパッケージが含まれています。 これらの更新プログラムは、次の CU リリースにも追加されます。

各 CU および GDR のリリースには、完全な SQL Server パッケージとそのリポジトリの以前のすべての更新が含まれています。 CU リリースに GDR のリリースから更新は、SQL Server 用に構成されているリポジトリを変更することによってサポートされています。 こともできます[ダウン グレード](sql-server-linux-setup.md#rollback)メジャー バージョン内で任意のリリースに (ex: 2017)。

> [!NOTE]
> CU GDR のリリースから更新できますリポジトリを変更することでいつでもリリースされます。 更新 CU から GDR リリースにリリースはサポートされていません。 

## <a name="change-to-a-ga-repository"></a>GA リポジトリへの変更します。

プレビュー リポジトリから 1 つのソース リポジトリ CU (GDR) に変更するには、次の手順を使用します。

1. 以前に構成されたプレビュー リポジトリを削除します。

   | プラットフォーム | リポジトリの削除 コマンド |
   |-----|-----|
   | RHEL | `sudo rm -rf /etc/yum.repos.d/mssql-server.repo` |
   | SLES | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
   | Ubuntu | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` |

1. **Ubuntu のみ**、パブリック リポジトリ鍵キーをインポートします。

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. 新しいリポジトリを構成します。

   | プラットフォーム | リポジトリ | Command |
   |-----|-----|-----|
   | RHEL | CU | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
   | RHEL | GDR | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |
   | SLES | CU  | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
   | SLES | GDR | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |
   | Ubuntu | CU | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)" && sudo apt-get update` |
   | Ubuntu | GDR | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)" && sudo apt-get update` |

1. [インストール](sql-server-linux-setup.md#platforms)または[更新](sql-server-linux-setup.md#upgrade)GA リポジトリを使用して SQL Server。

   > [!IMPORTANT]
   > 使用して、フル インストールを実行する場合、この時点で、[クイック スタート チュートリアル](#platforms)ターゲットのリポジトリを構成したことに注意してください。 チュートリアルではその手順は繰り返されません。 これは、クイック スタート チュートリアル CU リポジトリを使用するために GDR リポジトリを構成する場合に特に当てはまります。

## <a name="next-steps"></a>次の手順

Linux に SQL Server 2017 をインストールする方法の詳細については、次を参照してください。 [Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md)です。

