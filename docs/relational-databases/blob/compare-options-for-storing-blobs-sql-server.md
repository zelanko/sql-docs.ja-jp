---
title: "Blob (SQL Server) を保存するオプションの比較 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6038697b-36a9-49e8-a02a-2ad9e2e60e5a
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 98538bd77f81cd6a1f16857b70a866ee3f6d171a
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="compare-options-for-storing-blobs-sql-server"></a>Blob (SQL Server) を保存するオプションの比較
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
|**管理タスクのシングル ストーリー**|いいえ|可|**可**|  
|**サービスの単一セット**: 検索、レポート、クエリなど|いいえ|可|**可**|  
|**統合セキュリティ モデル**|いいえ|可|**可**|  
|**FILESTREAM データのインプレース更新**|可|いいえ|**可**|  
|**データベースで管理されるファイルおよびディレクトリの階層**|いいえ|いいえ|**可**|  
|**Windows アプリケーションの互換性**|可|いいえ|**可**|  
|**ファイルの属性へのリレーショナル アクセス**|いいえ|いいえ|**可**|  
  
##  <a name="CompareRBS"></a> FILESTREAM とリモート BLOB ストア (RBS) の比較  
 これらの 2 つの機能の比較については、RBS チームのブログ投稿「 [SQL Server リモート BLOB ストアと FILESTREAM 機能の比較](http://go.microsoft.com/fwlink/?LinkId=210317)」を参照してください。  
  
##  <a name="more"></a> その他の情報  
 [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)  
 [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)  
 [リモート BLOB ストア &#40;RBS&#41; &#40;SQL Server&#41;](../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
