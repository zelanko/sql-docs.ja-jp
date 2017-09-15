---
title: "Source プロパティ (ADO エラー) |Microsoft ドキュメント"
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
- Error::get_Source
- Error::Source
- Error::GetSource
helpviewer_keywords:
- Source property [ADO Error]
ms.assetid: 4044ba15-f013-4c4c-9fe1-b4410fe9a778
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 86c95ebdbacfffcee3e1be83c33ff3c5261352a6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="source-property-ado-error"></a>Source プロパティ (ADO エラー)
オブジェクトまたはエラーの発生源アプリケーションの名前を示します。  
  
## <a name="return-value"></a>戻り値  
 返します、**文字列**オブジェクトまたはアプリケーションの名前を示す値。  
  
## <a name="remarks"></a>解説  
 使用して、**ソース**プロパティを[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトまたはエラーの発生源アプリケーションの名前を決定するオブジェクト。 これは、オブジェクトのクラス名またはプログラム id です。 プロパティ値を指定する、ado エラー **ADODB** 。*ObjectName*ここで、 *ObjectName*エラーを発生させたオブジェクトの名前を指定します。 ADOX および ADO MD では、値になります**ADOX** 。*ObjectName*と**ADOMD** 。*ObjectName、*それぞれします。  
  
 エラーのドキュメントをに基づいて、**ソース**、[数](../../../ado/reference/ado-api/number-property-ado.md)、および[説明](../../../ado/reference/ado-api/description-property.md)のプロパティ**エラー**オブジェクトをコードを記述することができますエラーが適切に処理するされます。  
  
 **ソース**プロパティは読み取り専用です**エラー**オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>参照  
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (vc++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description プロパティ](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext、HelpFile プロパティ](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Number プロパティ (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source プロパティ (ADO レコード)](../../../ado/reference/ado-api/source-property-ado-record.md)   
 [Source プロパティ (ADO レコード セット)](../../../ado/reference/ado-api/source-property-ado-recordset.md)

