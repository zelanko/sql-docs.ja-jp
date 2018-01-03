---
title: "ODBC Jet エラー メッセージ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: error messages (ODBC driver for oracle)
ms.assetid: f8d2a8f2-0316-42c4-bc34-5367661634ae
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 206ebbdc1dd8a121f3c41f95cd305de6f4ef3d10
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-jet-error-messages"></a>ODBC Jet エラー メッセージ
データ ソースで発生したエラーの場合は、ODBC ドライバーは、ODBC ファイル ライブラリによって返されたエラー メッセージを返します。 ODBC ドライバーまたはドライバー マネージャーで発生したエラー、SQLSTATE と関連付けられたエラー メッセージがテキストに基づくドライバーを返します。  
  
 エラー メッセージでは、次の形式があります。  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 角かっこ () 内のプレフィックスは、エラーの場所を指定します。 ドライバー マネージャーで、エラーの発生時*データ ソース*は付与しません。 データ ソースでエラーが発生した場合、[*仕入先*] と [*ODBC コンポーネント*] プレフィックスは、仕入先と、データ ソースからのエラーが発生した ODBC コンポーネントの名前を識別します。  
  
 次の表は、ドライバー マネージャーとドライバー ISAM によって返されるエラー メッセージを示しています。  
  
|エラー メッセージ|エラーの場所|  
|-------------------|--------------------|  
|[Microsoft][ODBC ドライバー マネージャー]*メッセージ テキスト*|ドライバー マネージャー (Odbc32.dll)|  
|[Microsoft][ODBC*ドライバー名*]*メッセージ テキスト*|ドライバー ISAM (ドライバー Isam を参照してください)|
