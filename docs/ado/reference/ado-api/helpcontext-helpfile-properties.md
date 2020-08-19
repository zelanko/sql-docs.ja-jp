---
description: HelpContext、HelpFile プロパティ
title: HelpContext、HelpFile Properties |Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 628d3c0d01cc1b62304627fb310705b093976f8c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443484"
---
# <a name="helpcontext-helpfile-properties"></a>HelpContext、HelpFile プロパティ
[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトに関連付けられたヘルプファイルとトピックを示します。  
  
## <a name="return-values"></a>戻り値  
  
-   **HelpContextID** ヘルプファイル内のトピックのコンテキスト ID を **Long 型** の値として返します。  
  
-   **HelpFile** ヘルプファイルへの完全に解決されたパスに評価される **文字列** 値を返します。  
  
## <a name="remarks"></a>解説  
 ヘルプファイルが **HelpFile** プロパティに指定されている場合、 **helpcontext** プロパティを使用して、識別するヘルプトピックが自動的に表示されます。 関連するヘルプトピックが使用できない場合、 **Helpcontext** プロパティは0を返し、 **HelpFile** プロパティは長さ0の文字列 ("") を返します。  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>参照  
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description プロパティ](../../../ado/reference/ado-api/description-property.md)   
 [Number プロパティ (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source プロパティ (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)
