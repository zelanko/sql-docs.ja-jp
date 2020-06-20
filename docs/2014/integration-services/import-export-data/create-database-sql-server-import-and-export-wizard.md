---
title: '[データベースの作成] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createdatabase.f1
ms.assetid: 56a8a79f-086c-4bdc-8888-0045bb4b0cbf
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 8a2776d0288ef66214c9bdfd4218b924cb83c02b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965602"
---
# <a name="create-database-sql-server-import-and-export-wizard"></a>[データベースの作成] (SQL Server インポートおよびエクスポート ウィザード)
  [**データベースの作成**] ページを使用すると、変換先ファイルの新しいデータベースを定義できます。  
  
 このページでは、新しいデータベースの作成に利用できるオプションのサブセットが提供されます。 すべてのオプションを表示するには、を使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] します。  
  
 このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。 ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。  
  
 SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="options"></a>Options  
 **Name**  
 対象になる SQL Server データベースの一意な名前を指定します。 データベースに名前を付けるときは、必ず SQL Server の規約に従ってください。  
  
 **[データ ファイル名]**  
 データ ファイルの名前を表示します。 この名前は、指定されたデータベース名から派生されます。  
  
 **ログファイル名**  
 ログ ファイルの名前を表示します。 この名前は、指定されたデータベース名から派生されます。  
  
 **[初期サイズ] (データ ファイル)**  
 データ ファイルの初期サイズを MB 単位で指定します。  
  
 **[拡張を許可しない] (データ ファイル)**  
 指定した初期サイズを超えるデータ ファイルの拡張を許可するかどうかを示します。  
  
 **[比率で拡張する] (データ ファイル)**  
 データ ファイルの拡張を許可する比率を指定します。  
  
 **[サイズで拡張する] (データ ファイル)**  
 データ ファイルの拡張を許可するサイズを MB 単位で指定します。  
  
 **[初期サイズ] (ログ ファイル)**  
 ログ ファイルの初期サイズを MB 単位で指定します。  
  
 **[拡張を許可しない] (ログ ファイル)**  
 指定した初期サイズを超えるログ ファイルの拡張を許可するかどうかを示します。  
  
 **[比率で拡張する] (ログ ファイル)**  
 ログ ファイルの拡張を許可する比率を指定します。  
  
 **[サイズで拡張する] (ログ ファイル)**  
 ログ ファイルの拡張を許可するサイズを MB 単位で指定します。  
  
  
