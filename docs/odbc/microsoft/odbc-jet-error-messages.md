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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 85e0f9a8bc7015a0ad5b12ce46a6c94ab31ca43c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915814"
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
