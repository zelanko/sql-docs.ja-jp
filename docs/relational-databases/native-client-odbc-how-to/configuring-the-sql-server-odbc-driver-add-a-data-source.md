---
title: "データ ソース (ODBC) の追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e1e767e45e2899b855b564a91a723b929f5b8851
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="configuring-the-sql-server-odbc-driver---add-a-data-source"></a>SQL Server ODBC ドライバーのデータ ソースを追加の構成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降で ODBC アプリケーションを使用する前に、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でカタログ ストアド プロシージャのバージョンをアップグレードする方法や、データ ソースを追加、削除、およびテストする方法を理解しておく必要があります。  
  
  プログラムで ODBC アドミニストレーターを使用してデータ ソースを追加することができます (を使用して[SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md))、またはファイルを作成します。  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>ODBC アドミニストレーターを使用してデータ ソースを追加するには  
  
1.  **コントロール パネルの** 、アクセス**管理ツール**し**ODBC データ ソース (64 ビット)**または**ODBC データ ソース (32 ビット)**. または、odbcad32.exe を呼び出すことができます。  
  
2.  クリックして、**ユーザー DSN**、**システム DSN**、または**ファイル DSN**  タブをクリックして**追加**です。  
  
3.  をクリックして**SQL Server**をクリックし、**完了**です。  
  
4.  手順を完了、 **SQL Server に新しいデータ ソースを作成**ウィザード。  
  
### <a name="to-add-a-data-source-programmatically"></a>データ ソースをプログラムで追加するには  
  
1.  呼び出す[SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md) 2 番目のパラメーターを ODBC_ADD_DSN または ODBC_ADD_SYS_DSN に設定します。  
  
### <a name="to-add-a-file-data-source"></a>ファイル データ ソースを追加するには  
  
1.  呼び出す[SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) SAVEFILE = file_name パラメーター、接続文字列にします。 接続が確立されると、ODBC ドライバーによって、SAVEFILE パラメーターが指す場所の接続パラメーターを使用してファイル データ ソースが作成されます。  
  
## <a name="see-also"></a>参照  
[データ ソース &#40;ODBC&#41; を削除します。](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-delete-a-data-source.md)    
  
  
