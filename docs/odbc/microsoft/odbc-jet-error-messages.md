---
title: ODBC Jet エラーメッセージ |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81293112"
---
# <a name="odbc-jet-error-messages"></a>ODBC Jet エラー メッセージ
データソースで発生したエラーの場合、odbc ドライバーは ODBC ファイルライブラリによって返されたエラーメッセージを返します。 ODBC ドライバーまたはドライバーマネージャーで発生したエラーの場合、ドライバーは SQLSTATE に関連付けられているテキストに基づいてエラーメッセージを返します。  
  
 エラーメッセージの形式は次のとおりです。  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 角かっこ ([]) で囲まれたプレフィックスは、エラーの場所を識別します。 ドライバーマネージャーでエラーが発生した場合、*データソース*は指定されません。 データソースでエラーが発生すると、[*vendor*] プレフィックスと [*odbc-component*] プレフィックスによって、データソースからエラーを受け取った ODBC コンポーネントのベンダと名前が識別されます。  
  
 次の表は、ドライバーマネージャーとドライバー ISAM によって返されるエラーメッセージを示しています。  
  
|エラー メッセージ|エラーの場所|  
|-------------------|--------------------|  
|エクスプローラー[ODBC ドライバーマネージャー]*メッセージ-テキスト*|ドライバーマネージャー (Odbc32.dll)|  
|エクスプローラー[ODBC*ドライバー名*]*メッセージ-テキスト*|ドライバー ISAM (「ドライバーの ISAMs」を参照)|
