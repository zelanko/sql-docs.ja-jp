---
title: サポートされている内容の決定 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], Supports method
- Supports method [ADO]
ms.assetid: 65090cba-6d46-4775-8d61-f6838e7752a6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 835584da4c51f5e65306d0609b4e69f78a7d58b9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47707570"
---
# <a name="determining-what-is-supported"></a>サポートされている機能を特定する
**サポート**メソッドを使用して、指定したかどうかを判断**レコード セット**オブジェクトは、特定の種類の機能をサポートしています。 次の構文があります。  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="remarks"></a>コメント  
 **サポート**メソッドすべて CursorOptions 引数によって識別される機能のプロバイダーをサポートするかどうかを示すブール値を返します。 使用することができます、**サポート**機能の種類を特定する方法、**レコード セット**サポートしています。 場合、**レコード セット**オブジェクトが定数に対応するが、機能をサポートしている*CursorOptions*、**サポート**メソッドを返します**True。**. 返しますそれ以外の場合、 **False**します。  
  
 使用して、**サポート**メソッドの機能をチェックすることができます、**レコード セット**新しいレコードを追加、ブックマークを使用して、使用するオブジェクト、**検索**メソッドを使用して、スクロール、を使用します。**インデックス**プロパティ、およびバッチ更新を実行します。 定数とその意味の一覧は、次を参照してください。 [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)します。  
  
 ただし、**サポート**メソッドが返す可能性があります**True**の特定の機能が保証されないこと、プロバイダーが利用できる機能は、あらゆる状況下で。 **サポート**メソッドは単に特定の条件が満たされたと仮定した場合で、指定された機能をプロバイダーがサポートできるかどうかを返します。 など、**サポート**メソッドを示します、**レコード セット**オブジェクトは、カーソルは、複数のテーブル結合に基づいて場合でも、更新プログラムをサポートしています: 一部の列は更新不可能な。
