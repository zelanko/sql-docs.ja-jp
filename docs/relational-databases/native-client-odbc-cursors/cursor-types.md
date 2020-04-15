---
title: カーソルの種類 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4782c61c2f150e36c9632d09170468229c238cbb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305490"
---
# <a name="cursor-types"></a>カーソルの種類
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC では、マイクロソフト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]およびネイティブ クライアント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ODBC ドライバーでサポートされている 4 つのカーソルの種類を定義します。 これらのカーソルは、結果セットの変更を検出する機能と **、tempdb**のメモリや領域など、それらが消費するリソースで異なります。 カーソルが行への変更を検出できるのは、変更が加えられた行の再フェッチを試みたときだけです。現在フェッチしている行への変更を、データ ソースからカーソルに通知する方法はありません。 カーソルを使用して行われなかった変更を検出する機能は、トランザクション分離レベルによって異なる場合があります。  
  
 次に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされる 4 種類の ODBC カーソルを示します。  
  
-   順方向専用カーソルではスクロールがサポートされず、カーソルの最初から最後まで行を順番にフェッチする機能だけがサポートされます。  
  
-   静的カーソルは、カーソルが開かれると**tempdb**に作成されます。 静的カーソルは、常に、カーソルを開いた時点の結果セットを表示します。 データへの変更は反映されません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の静的カーソルは常に読み取り専用です。 静的サーバー カーソルは**tempdb**の作業テーブルとして構築されるため、カーソル結果セットのサイズは、 で許可されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]最大行サイズを超えることはできません。  
  
-   キーセット ドリブン カーソルでは、カーソルを開くときに、結果セット内の行のメンバーシップと順序が固定されます。 非キー列の変更は、このカーソルを使用して表示されます。  
  
-   動的カーソルは静的カーソルと対照的です。 動的カーソルでは、結果セット内の行に対するすべての変更が反映されます。 結果セット内の行のデータ値、順序、およびメンバーシップは、フェッチを実行するたびに変化する可能性があります。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;カーソルの使用](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
