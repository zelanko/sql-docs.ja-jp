---
title: "以下のプロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Error::GetNativeError
- Error::get_NativeError
- Error::NativeError
helpviewer_keywords: NativeError property [ADO]
ms.assetid: b9b47e57-18a4-4186-aef5-5bd18d7b1d74
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 55a6415051943de6b92327ce4e9cf157c972edd4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="nativeerror-property-ado"></a>以下のプロパティ (ADO)
プロバイダー固有のエラー コードを示す、指定された[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 返します、**長い**エラー コードを示す値。  
  
## <a name="remarks"></a>解説  
 使用して、**以下**、特定のデータベースに固有のエラー情報を取得するプロパティを**エラー**オブジェクト。 たとえば、OLE DB 用 Microsoft ODBC プロバイダーを使用して、Microsoft SQL Server データベースと、SQL Server から送られたネイティブ エラー コードへのパススルー ODBC と ODBC プロバイダー、ADO**以下**プロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>参照  
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (vc++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
