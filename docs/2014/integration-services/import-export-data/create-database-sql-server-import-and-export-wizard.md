---
title: '[データベースの作成] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.impexpwizard.createdatabase.f1
ms.assetid: 56a8a79f-086c-4bdc-8888-0045bb4b0cbf
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a2af52bdfbb4e6e2a2f5b069ff4555fbce7315bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082796"
---
# <a name="create-database-sql-server-import-and-export-wizard"></a>[データベースの作成] (SQL Server インポートおよびエクスポート ウィザード)
  使用して、 **Create Database**コピー先ファイルの新しいデータベースを定義するページ。  
  
 このページでは、新しいデータベースの作成に利用できるオプションのサブセットが提供されます。 表示するには、すべてのオプションを使用して[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。  
  
 このウィザードの詳細については、次を参照してください。 [SQL Server インポートおよびエクスポート ウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)です。 について、ウィザードを起動するオプションおよびウィザードが正常に実行するための権限については、次を参照してください。 [、SQL Server インポートおよびエクスポート ウィザードを実行](start-the-sql-server-import-and-export-wizard.md)です。  
  
 SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="options"></a>および  
 **Name**  
 対象になる SQL Server データベースの一意な名前を指定します。 データベースに名前を付けるときは、必ず SQL Server の規約に従ってください。  
  
 **データ ファイル名**  
 データ ファイルの名前を表示します。 この名前は、指定されたデータベース名から派生されます。  
  
 **ログ ファイルの名前**  
 ログ ファイルの名前を表示します。 この名前は、指定されたデータベース名から派生されます。  
  
 **初期サイズ (データ ファイル)**  
 データ ファイルの初期サイズを MB 単位で指定します。  
  
 **拡張を許可しない (データ ファイル)**  
 指定した初期サイズを超えるデータ ファイルの拡張を許可するかどうかを示します。  
  
 **比率で拡張 (データ ファイル)**  
 データ ファイルの拡張を許可する比率を指定します。  
  
 **サイズ (データ ファイル) で拡張します。**  
 データ ファイルの拡張を許可するサイズを MB 単位で指定します。  
  
 **初期サイズ (ログ ファイル)**  
 ログ ファイルの初期サイズを MB 単位で指定します。  
  
 **拡張を許可しない (ログ ファイル)**  
 指定した初期サイズを超えるログ ファイルの拡張を許可するかどうかを示します。  
  
 **比率で拡張 (ログ ファイル)**  
 ログ ファイルの拡張を許可する比率を指定します。  
  
 **サイズ (ログ ファイル) で拡張します。**  
 ログ ファイルの拡張を許可するサイズを MB 単位で指定します。  
  
  