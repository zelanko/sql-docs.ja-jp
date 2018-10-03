---
title: SQL Server 変換先のカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: b736aa6d-c154-44a0-be08-f25733fca1d9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 56a0d3af834d19b1ec917d6f8c765c1e7755934f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48146952"
---
# <a name="sql-server-destination-custom-properties"></a>SQL Server 変換先のカスタム プロパティ
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントに共通するプロパティの両方があります。  
  
 次の表は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|説明|  
|-------------------|---------------|-----------------|  
|AlwaysUseDefaultCodePage|ブール値|DefaultCodePage プロパティ値を強制的に使用します。 このプロパティの既定値は`False`します。|  
|BulkInsertCheckConstraints|ブール値|一括挿入で制約をチェックするかどうかを指定する値。 このプロパティの既定値は`True`します。|  
|BulkInsertFireTriggers|ブール値|一括挿入でテーブル上のトリガーを起動するかどうかを指定する値。 このプロパティの既定値は`False`します。|  
|BulkInsertFirstRow|Integer|挿入する最初の行を指定する値。 このプロパティの既定値は、 **-1**です。これは、割り当てられた値がないことを示します。|  
|BulkInsertKeepIdentity|ブール値|ID 列に値を挿入できるかどうかを指定する値。 このプロパティの既定値は`False`します。|  
|BulkInsertKeepNulls|ブール値|一括挿入で NULL 値を保持するかどうかを指定する値。 このプロパティの既定値は`False`します。|  
|BulkInsertLastRow|Integer|挿入する最後の行を指定する値。 このプロパティの既定値は、 **-1**です。これは、割り当てられた値がないことを示します。|  
|BulkInsertMaxErrors|Integer|一括挿入を停止する前に許容するエラー数を指定する値。 このプロパティの既定値は、 **-1**です。これは、割り当てられた値がないことを示します。|  
|BulkInsertOrder|String|並べ替え列の名前。 各列は、昇順または降順で並べ替えることができます。 並べ替え列を複数使用する場合、列の名前はコンマで区切ります。|  
|BulkInsertTableName|String|データのコピー先となる、データベース内の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルまたはビュー。|  
|BulkInsertTablock|ブール値|一括挿入中にテーブルをロックするかどうかを指定する値。 このプロパティの既定値は`True`します。|  
|DefaultCodePage|Integer|コード ページに関する情報をデータ ソースから取得できない場合に使用するコード ページ。|  
|MaxInsertCommitSize|Integer|バッチに挿入する行の最大数を示す値。 値がゼロのときは、単一のバッチにすべての行が挿入されます。|  
|Timeout|Integer|挿入できるデータがない場合、終了前に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先が待機する秒数を指定する値。 値を 0 に設定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先はタイムアウトしません。このプロパティの既定値は 30 です。|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [SQL Server 変換先](sql-server-destination.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](../common-properties.md)  
  
  
