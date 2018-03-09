---
title: "Blob (SQL Server) を保存するオプションの比較 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: blob
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6038697b-36a9-49e8-a02a-2ad9e2e60e5a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5b32325de1691fae92ff7bcecfeeda305df98d31
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="compare-options-for-storing-blobs-sql-server"></a>Blob (SQL Server) を保存するオプションの比較
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
ファイルおよびドキュメントを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に格納するために使用できるオプションを説明して比較します。  
  
##  <a name="Expectations"></a> データベースへのファイルの格納 - 利点と予測  
 企業データの大部分は、実際は構造化されておらず、通常、ファイルや文書としてファイル システムに保存されています。 このデータの大半は、Windows API を通じてファイルにアクセスするアプリケーションによって作成、管理、および使用されます。 通常、企業はこのデータをファイル システムに保存し、ファイルの関連するメタデータ ファイルをリレーショナル データベースに格納します。  
  
 非構造化データをリレーショナル データベースに統合すると、大きな利点があります。 これらの利点には、次のようなものがあります。  
  
-   バックアップなどの、統合ストレージおよびデータ管理機能。  
  
-   データとメタデータ全体に対するフルテキスト検索、セマンティック検索などの統合サービス。  
  
-   非構造化データの管理およびポリシーの管理の容易さ。  
  
 しかし、ほとんどの場合、非構造化データをリレーショナル データベースに格納するのは便利ではありませんでした。 これまでは、既存の Windows ベースのアプリケーションをリレーショナル システム上で実行することは不可能でした。 既に確立されているアプリケーション (Microsoft Word、Adobe Reader など) をリレーショナル データベース API 上で実行するように書き直すのは現実的ではありません。 このようなアプリケーションでは、単純に、データが Windows API を通じてアクセスされることが前提となっています。 つまり、次のような前提です。  
  
-   Windows アプリケーションにはデータベース トランザクションが不要であり、認識もされない。  
  
-   Windows アプリケーションは、ファイルおよびディレクトリ データのためにファイル システム API との互換性が必要。  
  
##  <a name="Filestream"></a> FILESTREAM  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、ファイル システムでファイルとして格納される非構造化データの効率的な保管、管理、およびストリーミングを可能にする FILESTREAM 機能が既に装備されています。 ただし、FILESTREAM ソリューションはカスタム プログラミングを必要とし、上で説明した完全な Windows アプリケーションの互換性の要件を満たしていません。  
  
##  <a name="FileTables"></a> FileTables  
 FileTable 機能は、既存の FILESTREAM 機能をベースとして構築されています。企業は、FileTable 機能を使用することにより、非トランザクション アクセスやファイルベース データの Windows アプリケーションの互換性の要件を解決して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の非構造化ファイル データおよびディレクトリ階層を格納できるようになります。  
  
##  <a name="CompareFileTable"></a> FILESTREAM と FileTable の比較  
  
|機能|ファイル サーバーとデータベース ソリューション|FILESTREAM ソリューション|FileTable ソリューション|  
|-------------|---------------------------------------|-------------------------|------------------------|  
|**管理タスクのシングル ストーリー**|いいえ|はい|**はい**|  
|**サービスの単一セット**: 検索、レポート、クエリなど|いいえ|はい|**はい**|  
|**統合セキュリティ モデル**|いいえ|はい|**可**|  
|**FILESTREAM データのインプレース更新**|はい|いいえ|**はい**|  
|**データベースで管理されるファイルおよびディレクトリの階層**|いいえ|いいえ|**はい**|  
|**Windows アプリケーションの互換性**|はい|いいえ|**可**|  
|**ファイルの属性へのリレーショナル アクセス**|いいえ|いいえ|**はい**|  
  
##  <a name="CompareRBS"></a> FILESTREAM とリモート BLOB ストア (RBS) の比較  
 これらの 2 つの機能の比較については、RBS チームのブログ投稿「 [SQL Server リモート BLOB ストアと FILESTREAM 機能の比較](http://go.microsoft.com/fwlink/?LinkId=210317)」を参照してください。  
  
##  <a name="more"></a> その他の情報  
 [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)  
 [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)  
 [リモート BLOB ストア &#40;RBS&#41; &#40;SQL Server&#41;](../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
