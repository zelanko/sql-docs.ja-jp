---
title: Source プロパティ (ADO Error) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::get_Source
- Error::Source
- Error::GetSource
helpviewer_keywords:
- Source property [ADO Error]
ms.assetid: 4044ba15-f013-4c4c-9fe1-b4410fe9a778
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6b55ebbe5a167b7d70cf606fc4e37e7ede36b486
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67916900"
---
# <a name="source-property-ado-error"></a>Source プロパティ (ADO Error)
最初にエラーを生成したオブジェクトまたはアプリケーションの名前を示します。  
  
## <a name="return-value"></a>戻り値  
 オブジェクトまたはアプリケーションの名前を示す**文字列**値を返します。  
  
## <a name="remarks"></a>解説  
 [エラーオブジェクトの](../../../ado/reference/ado-api/error-object.md) **Source**プロパティを使用して、最初にエラーを生成したオブジェクトまたはアプリケーションの名前を確認します。 オブジェクトのクラス名またはプログラム ID を指定できます。 ADO のエラーの場合、プロパティ値は ADODB になり**ます。**_Objectname_。ここで、 *objectname*はエラーを発生させたオブジェクトの名前です。 ADOX と ADO MD の場合、この値は**adox になります。**_ObjectName_と**ADOMD。**_ObjectName_。  
  
 **Error オブジェクトの** **Source**、 [Number](../../../ado/reference/ado-api/number-property-ado.md)、 [Description](../../../ado/reference/ado-api/description-property.md)プロパティからのエラードキュメントに基づいて、エラーを適切に処理するコードを記述できます。  
  
 **Source**プロパティは、**エラー**オブジェクトの場合は読み取り専用です。  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>参照  
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description プロパティ](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext、HelpFile プロパティ](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Number プロパティ (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source プロパティ (ADO Record)](../../../ado/reference/ado-api/source-property-ado-record.md)   
 [Source プロパティ (ADO Recordset)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
