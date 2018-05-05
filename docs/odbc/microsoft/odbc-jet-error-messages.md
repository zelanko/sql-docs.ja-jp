---
title: ODBC Jet エラー メッセージ |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- error messages (ODBC driver for oracle)
ms.assetid: f8d2a8f2-0316-42c4-bc34-5367661634ae
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0f487fce920dd82fc36e460467733393ffdbbc36
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
