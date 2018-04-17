---
title: データ型の制限事項 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], data types
- data types [ODBC], desktop database drivers
- desktop database drivers [ODBC], data types
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f7be82a89d81f887baf0ae6ef0fe7cd00e72c27
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
|TIMESTAMP|TIMESTAMP データ型は、CONVERT 関数によってそれ自体に変換できません。|  
|TINYINT|TINYINT 値は常に符号付きではありません。|  
|長さ 0 の文字列|DBASE、Excel、Paradox、または Textdriver 使用すると、長さ 0 の文字列を列に挿入実際には NULL が挿入、代わりにします。|
