---
title: "\"メッセージのエラー\" プロパティ (ADO) |Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetNativeError
- Error::get_NativeError
- Error::NativeError
helpviewer_keywords:
- NativeError property [ADO]
ms.assetid: b9b47e57-18a4-4186-aef5-5bd18d7b1d74
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 42888190dcd7b5e41987e6e8ec7194242549aa9c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918024"
---
# <a name="nativeerror-property-ado"></a>NativeError プロパティ (ADO)
特定の[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトのプロバイダー固有のエラーコードを示します。  
  
## <a name="return-value"></a>戻り値  
 エラーコードを示す**Long 型**の値を返します。  
  
## <a name="remarks"></a>Remarks  
 特定の**エラー**オブジェクトのデータベース固有のエラー情報を取得するには、"**エラー** " プロパティを使用します。 たとえば、Microsoft SQL Server データベースと共に Microsoft ODBC Provider for OLE DB を使用する場合、SQL Server からのネイティブエラーコードによって、ODBC および ODBC プロバイダーから ADO の "**エラー** " プロパティに渡されます。  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>参照  
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
