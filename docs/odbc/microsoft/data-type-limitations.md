---
title: "データ型の制限事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], data types
- data types [ODBC], desktop database drivers
- desktop database drivers [ODBC], data types
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 558789a4f435e9fc54176b1423d71369f6b4cc22
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="data-type-limitations"></a>データ型の制限事項
Microsoft ODBC のデスクトップ データベース ドライバーでは、データ型で、次の制限を課します。  
  
|データ型|Description|  
|---------------|-----------------|  
|すべてのデータ型|型変換に失敗すると、影響を受ける列を NULL に設定されている可能性があります。|  
|BINARY|長さ 0 のバイナリ列の作成と、255 バイトのバイナリ列実際に返されます。|  
|[DATE]|DATE データ型は、CONVERT 関数が別のデータ型 (または自体) に変換できません。|  
|10 進数 (正確な数値)|サポートされていません。|  
|浮動小数点データ型|浮動小数点数の小数点以下桁数は、Windows のコントロール パネルの国際化のセクションで設定する数値書式によって制限可能性があります。|  
|NUMERIC|最大有効桁数と小数点以下桁数は 28 をサポートしています。|  
|timestamp|TIMESTAMP データ型は、CONVERT 関数によってそれ自体に変換できません。|  
|TINYINT|TINYINT 値は常に符号付きではありません。|  
|長さ 0 の文字列|DBASE、Excel、Paradox、または Textdriver 使用すると、長さ 0 の文字列を列に挿入実際には NULL が挿入、代わりにします。|

