---
title: "メソッドをサポートしています |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::raw_Supports
- Recordset15::Supports
helpviewer_keywords:
- Supports method [ADO]
ms.assetid: 298fc41c-0b55-42fc-b373-c5133b4da6a5
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 60e3039e48ea203b0585dba1ecbeaf7ad3e57907
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="supports-method"></a>メソッドをサポートしています
指定したかどうかを決定[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトは、特定の種類の機能をサポートしています。  
  
## <a name="syntax"></a>構文  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="return-value"></a>戻り値  
 返します、**ブール**で識別されるすべての機能かどうかを示す値、 *CursorOptions*引数は、プロバイダーによってサポートされています。  
  
#### <a name="parameters"></a>パラメーター  
 *CursorOptions*  
 A**長い**を 1 つ以上で構成される式[CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)値。  
  
## <a name="remarks"></a>解説  
 使用して、**をサポートしている**機能の種類を特定する方法、 **Recordset**サポートしています。 場合、 **Recordset**オブジェクトを定数に対応するが、機能をサポートしている*CursorOptions*、**をサポートしている**メソッドを返します**をTrue。**. 返しますそれ以外の場合、 **False**です。  
  
> [!NOTE]
>  **サポート**メソッドが返す可能性があります**True**の特定の機能とは限りませんプロバイダーは、実行できること、機能のすべての状況で使用可能な。 **サポート**メソッドは単に特定の条件が満たされたと仮定した場合で、指定された機能をプロバイダーがサポートできるかどうかを返します。 たとえば、**をサポートしている**メソッド可能性があります、**レコード セット**カーソルは一部の列は更新できない複数のテーブル結合に基づいている場合でも、オブジェクトが更新をサポートします。  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [メソッドの例 (VB) をサポートしています](../../../ado/reference/ado-api/supports-method-example-vb.md)   
 [メソッドの例 (vc++) をサポートしています](../../../ado/reference/ado-api/supports-method-example-vc.md)   
 [カーソル。 プロパティ (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)

