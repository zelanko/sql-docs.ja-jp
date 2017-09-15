---
title: "Description プロパティ |Microsoft ドキュメント"
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
- Error::Description
- Error::GetDescription
- Error::get_Description
helpviewer_keywords:
- Description property
ms.assetid: 4b5d6790-6c29-42aa-bf78-d9cfb8ad7965
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5fe6e991baea65a345a6e3a070165dfa568982c4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="description-property"></a>Description プロパティ
について説明します、[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 返します、**文字列**エラーの説明を含む値です。  
  
## <a name="remarks"></a>解説  
 使用して、**説明**エラーの簡単な説明を取得するプロパティです。 ユーザーができない場合や、処理したくないエラーのアラートを生成するには、このプロパティを表示します。 文字列は、ADO またはプロバイダーのいずれかから取得されます。  
  
 プロバイダーは、ADO に特定のエラー テキストを渡すことを担当します。 ADO を追加、[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトを**エラー**コレクション プロバイダーごとにエラーまたは警告を受信します。 列挙、**エラー**プロバイダーに合格するエラーをトレースするコレクション。  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>参照  
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (vc++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [HelpContext、HelpFile プロパティ](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Number プロパティ (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source プロパティ (ADO エラー)](../../../ado/reference/ado-api/source-property-ado-error.md)

