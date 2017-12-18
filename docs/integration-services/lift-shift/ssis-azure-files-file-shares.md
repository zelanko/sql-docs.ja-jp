---
title: "オンプレミスおよび Azure のファイル共有のファイルを格納および取得する | Microsoft Docs"
description: "この記事では、SSIS でオンプレミスと Azure 両方のファイル システムおよびファイル共有を使う方法について説明します"
ms.date: 11/10/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4980f39deea4d70817da3650dccbff7997ba83d
ms.sourcegitcommit: 06bb91d138a4d6395c7603a2d8f99c69a20642d3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2017
---
# <a name="store-and-retrieve-files-on-file-shares-on-premises-and-in-azure-with-ssis"></a>オンプレミスおよび Azure のファイル共有のファイルを格納および取得する
この記事では、ローカル ファイル システムを使う SQL Server Integration Services (SSIS) パッケージを Azure にリフト アンド シフトするときにパッケージを更新する方法について説明します。

> [!IMPORTANT]
> 現時点では、SSIS カタログ データベース (SSISDB) はアクセス資格情報を 1 セットだけサポートします。 したがって、Azure-SSIS Integration Runtime (IR) は、複数のオンプレミスのファイル共有および Azure Files 共有に、異なる資格情報を使って接続することはできません。

## <a name="store-temporary-files"></a>一時ファイルを格納する
単一のパッケージ実行の間に一時ファイルを格納して処理する必要がある場合、パッケージは Azure-SSIS Integration Runtime ノードの一時フォルダー `(.)/temp` または `%TEMP%` を使うことができます。

## <a name="store-files-across-multiple-package-executions"></a>複数のパッケージ実行の間でファイルを格納する
永続的なファイルを格納して処理し、それらを複数のパッケージ実行にわたって保持する必要がある場合は、オンプレミスのファイル共有または Azure Files を使うことができます

### <a name="use-on-premises-file-shares"></a>オンプレミスのファイル共有を使う
ローカル ファイル システムを使うパッケージを Azure の SSIS にリフト アンド シフトするときに、引き続き**オンプレミスのファイル共有**を使うには、次のようにします。
1.  ローカル ファイル システムからオンプレミスのファイル共有にファイルを転送します。
2.  オンプレミスのファイル共有を Azure Virtual Network (VNet) に参加させます。
3.  Azure-SSIS IR を同じ VNet に参加させます。 詳しくは、「[Azure-SSIS 統合ランタイムを仮想ネットワークに参加させる](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network)」をご覧ください。
4.  Windows 認証を使うアクセス資格情報を設定することにより、同じ VNet 内のオンプレミスのファイル共有に Azure SSIS IR を接続します。 詳しくは、「[Windows 認証でオンプレミス データ ソースと Azure ファイル共有に接続する](ssis-azure-connect-with-windows-auth.md)」をご覧ください。
5.  パッケージ内のローカル ファイル パスを、オンプレミスのファイル共有を指す UNC パスに更新します。 たとえば、`C:\abc.txt` を `\\<on-prem-server-name>\<share-name>\abc.txt` に更新します。

### <a name="use-azure-file-shares"></a>Azure Files 共有を使用する
ローカル ファイル システムを使うパッケージを Azure の SSIS にリフト アンド シフトするときに、**Azure Files** を使うには、次のようにします。
1.  ローカル ファイル システムから Azure Files にファイルを転送します。 詳しくは、「[Azure ファイル](https://azure.microsoft.com/services/storage/files/)」をご覧ください。
2.  Windows 認証を使うアクセス資格情報を設定することにより、Azure Files に Azure SSIS IR を接続します。 詳しくは、「[Windows 認証でオンプレミス データ ソースと Azure ファイル共有に接続する](ssis-azure-connect-with-windows-auth.md)」をご覧ください。
3.  パッケージ内のローカル ファイル パスを、Azure Files を指す UNC パスに更新します。 たとえば、`C:\abc.txt` を `\\<storage-account-name>.file.core.windows.net\<share-name>\abc.txt` に更新します。
