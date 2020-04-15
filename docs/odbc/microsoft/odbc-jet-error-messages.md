---
title: ODBC ジェット のエラー メッセージ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages (ODBC driver for oracle)
ms.assetid: f8d2a8f2-0316-42c4-bc34-5367661634ae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e8fa6e672b69c7791e66dc3919e6fcd22b7c3de7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293112"
---
# <a name="odbc-jet-error-messages"></a>ODBC Jet エラー メッセージ
データ ソースで発生したエラーの場合、ODBC ドライバーは ODBC ファイル ライブラリから返されるエラー メッセージを返します。 ODBC ドライバーまたはドライバー マネージャーで発生するエラーの場合、ドライバーは、SQLSTATE に関連付けられているテキストに基づいてエラー メッセージを返します。  
  
 エラー メッセージの形式は次のとおりです。  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 括弧 ([]) 内の接頭辞は、エラーの位置を示します。 ドライバ マネージャでエラーが発生した場合、*データ ソース*は指定されません。 データ ソースでエラーが発生すると、"*ベンダ*] と *[ODBC コンポーネント*] のプレフィックスが、データ ソースからエラーを受け取った ODBC コンポーネントのベンダ名と名前を示します。  
  
 次の表は、ドライバー マネージャーとドライバーの ISAM によって返されるエラー メッセージを示します。  
  
|エラー メッセージ|エラーの場所|  
|-------------------|--------------------|  
|[マイクロソフト][ODBC ドライバー マネージャー]*メッセージ テキスト*|ドライバー マネージャー (Odbc32.dll)|  
|[マイクロソフト][ODBC*ドライバ名*]*メッセージ テキスト*|ドライバ ISAM (ドライバ ISAM を参照)|
