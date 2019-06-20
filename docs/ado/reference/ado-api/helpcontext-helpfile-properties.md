---
title: HelpContext、HelpFile プロパティ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c9c980e293b06e7fa9642ace7d425b7ffd3c0197
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66694808"
---
# <a name="helpcontext-helpfile-properties"></a>HelpContext、HelpFile プロパティ
ヘルプ ファイルと関連付けられているトピックを示します、[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。  
  
## <a name="return-values"></a>戻り値  
  
-   **ヘルプ コンテキスト Id**として、コンテキスト ID を返します、**長い**トピックでは、ヘルプ ファイル内の値。  
  
-   **HelpFile**返します、**文字列**ヘルプ ファイルへの完全に解決されたパスに評価される値。  
  
## <a name="remarks"></a>コメント  
 ヘルプ ファイルがで指定されている場合、 **HelpFile**プロパティ、 **HelpContext**プロパティが自動的に識別するヘルプ トピックを表示するために使用します。 使用可能な関連するヘルプ トピックがない場合、 **HelpContext**プロパティは 0 を返します、 **HelpFile**プロパティは、長さ 0 の文字列を返します ("")。  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>参照  
 [Description、HelpContext、HelpFile、NativeError、数、ソース、および SQLState プロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description、HelpContext、HelpFile、NativeError、数、ソース、および SQLState プロパティの例 (vc++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description プロパティ](../../../ado/reference/ado-api/description-property.md)   
 [Number プロパティ (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source プロパティ (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)
