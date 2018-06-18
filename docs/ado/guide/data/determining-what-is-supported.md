---
title: サポートされている機能を決定する |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], Supports method
- Supports method [ADO]
ms.assetid: 65090cba-6d46-4775-8d61-f6838e7752a6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d6eaf6ed08d6e79f8428e86b983794cb32c6447d
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270591"
---
# <a name="determining-what-is-supported"></a>サポートされている機能を決定します。
**をサポートしている**メソッドを使用して、指定したかどうかを判断**Recordset**オブジェクトは、特定の種類の機能をサポートしています。 次の構文があります。  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="remarks"></a>コメント  
 **サポート**メソッドすべて CursorOptions 引数によって示されている機能のプロバイダーがサポートするかどうかを示すブール値を返します。 使用することができます、**をサポートしている**機能の種類を特定する方法、 **Recordset**サポートしています。 場合、 **Recordset**オブジェクトを定数に対応するが、機能をサポートしている*CursorOptions*、**をサポートしている**メソッドを返します**をTrue。**. 返しますそれ以外の場合、 **False**です。  
  
 使用して、**サポート**メソッドの機能を確認することができます、 **Recordset**新しいレコードを追加、ブックマークを使用して、使用するオブジェクト、**検索**方法、スクロールを使用して、を使用します。**インデックス**プロパティ、およびバッチ更新を実行します。 定数とその意味の一覧については、次を参照してください。 [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)です。  
  
 **サポート**メソッドが返す可能性があります**True**の特定の機能とは限りませんプロバイダーは、実行できること、機能のすべての状況で使用可能な。 **サポート**メソッドは単に特定の条件が満たされたと仮定した場合で、指定された機能をプロバイダーがサポートできるかどうかを返します。 たとえば、**をサポートしている**メソッド可能性があります、**レコード セット**オブジェクトは、カーソルは、複数のテーブル結合に基づいている場合でも、更新をサポートしている — 一部の列は更新不可能なです。
