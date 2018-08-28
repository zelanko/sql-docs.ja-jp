---
title: 一括インポートまたは一括エクスポートのデータ形式 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: import-export
ms.reviewer: ''
ms.suite: sql
ms.technology: data-movement
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], choosing
- bulk importing [SQL Server], data formats
ms.assetid: 73fe6741-9437-4b26-b030-28b863e74399
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d148f0e2c3952056d0394823ad398cfb17bd48cb
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43090184"
---
# <a name="data-formats-for-bulk-import-or-bulk-export-sql-server"></a>一括インポートまたは一括エクスポートのデータ形式 (SQL Server)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、データを文字データ形式でもネイティブ バイナリ データ形式でも受け取ることができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と別のアプリケーション ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel など) または別のデータベース サーバー (Oracle や [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]など) との間でデータを移動するときは、文字形式を使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス間でデータを転送する場合にのみ、ネイティブ形式を使用できます。  
  
 **このトピックの内容**  
  
-   [一括インポートまたは一括エクスポートのデータ形式](#ComponentsAndConcepts)  
  
-   [関連タスク](#RelatedTasks)  
  
##  <a name="ComponentsAndConcepts"></a> 一括インポートまたは一括エクスポートのデータ形式  
 次の表は、データの表現方法や転送元または転送先に基づいて、一般的にどのデータ形式を使用するのが適切かを示しています。  
  
|演算|ネイティブ|Unicode ネイティブ|文字|Unicode 文字|  
|---------------|------------|--------------------|---------------|-----------------------|  
|拡張文字や 2 バイト文字セット (DBCS) の文字を含まないデータ ファイルを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンス間でデータを一括転送します。 フォーマット ファイルを使用する場合を除いて、これらのテーブルは同じように定義されている必要があります。|可*|—|—|—|  
|文字形式や Unicode 形式とは異なり、ネイティブ データ形式では各 **sql_variant** 値のメタデータが保持されるので、 **sql_variant** 列ではネイティブ データ形式を使用することが最も適しています。|[ユーザー アカウント制御]|—|—|—|  
|拡張文字や DBCS 文字を含むデータ ファイルを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンス間でデータを一括転送します。|—|[ユーザー アカウント制御]|—|—|  
|別のプログラムで生成されたテキスト ファイルからデータを一括インポートします。|—|—|[ユーザー アカウント制御]|—|  
|別のプログラムで使用するテキスト ファイルにデータを一括エクスポートします。|—|—|[ユーザー アカウント制御]|—|  
|Unicode データを含み、拡張文字や DBCS 文字は含まないデータ ファイルを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンス間でデータを一括転送します。|—|—|—|[ユーザー アカウント制御]|  
  
 \*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bcp **を使用して**からデータを最も速く一括エクスポートできる方法です。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート](../../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [bcp を使用した互換性のためのデータ形式の指定 &#40;SQL Server&#41;](../../relational-databases/import-export/specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)  
  
  
