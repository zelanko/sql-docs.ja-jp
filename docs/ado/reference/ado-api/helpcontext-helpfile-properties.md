---
title: HelpContext、HelpFile プロパティ |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetHelpContext
- Error::GetHelpFile
- Error::get_HelpFile
- Error::get_HelpContext
- Error::HelpContext
- Error::HelpFile
helpviewer_keywords:
- HelpContext property [ADO]
- HelpFile property [ADO]
ms.assetid: 2b9ef441-993c-44d4-8f87-fac0979dac1d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0fdd4316a0d1ca1e75b074590755a65267e93ca0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="helpcontext-helpfile-properties"></a>HelpContext、HelpFile プロパティ
ヘルプ ファイルとに関連付けられているトピックを示します、[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。  
  
## <a name="return-values"></a>戻り値  
  
-   **ヘルプ コンテキスト Id**として、コンテキスト ID を返します、**長い**ヘルプ ファイルのトピックの値。  
  
-   **HelpFile**を返します、**文字列**ヘルプ ファイルを完全に解決されたパスに評価される値。  
  
## <a name="remarks"></a>解説  
 ヘルプ ファイルが指定されている場合、 **HelpFile** 、プロパティ、 **HelpContext**プロパティの使用に自動的に識別するヘルプ トピックを表示します。 使用可能な関連するヘルプ トピックがない場合、 **HelpContext**プロパティは 0 を返しますと**HelpFile**プロパティが長さ 0 の文字列を返します ("") です。  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>参照  
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (vc++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description プロパティ](../../../ado/reference/ado-api/description-property.md)   
 [Number プロパティ (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source プロパティ (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)
