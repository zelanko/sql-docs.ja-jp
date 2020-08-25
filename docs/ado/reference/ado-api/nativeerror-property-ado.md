---
description: NativeError プロパティ (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c22667a9cd5855e4715b8aa37774a9137ab3cc4
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774061"
---
# <a name="nativeerror-property-ado"></a>NativeError プロパティ (ADO)
特定の [エラー](./error-object.md) オブジェクトのプロバイダー固有のエラーコードを示します。  
  
## <a name="return-value"></a>戻り値  
 エラーコードを示す **Long 型** の値を返します。  
  
## <a name="remarks"></a>解説  
 特定の**エラー**オブジェクトのデータベース固有のエラー情報を取得するには、"**エラー** " プロパティを使用します。 たとえば、Microsoft SQL Server データベースと共に Microsoft ODBC Provider for OLE DB を使用する場合、SQL Server からのネイティブエラーコードによって、ODBC および ODBC プロバイダーから ADO の " **エラー** " プロパティに渡されます。  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](./error-object.md)  
  
## <a name="see-also"></a>参照  
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VB)](./description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VC + +)](./description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)