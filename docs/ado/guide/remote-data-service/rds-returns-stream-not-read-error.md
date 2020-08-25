---
description: RDS &quot; はストリームの読み取り不可エラーを返します &quot;
title: RDS &quot; はストリーム Not Read エラーを返します。 &quot; Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stream not read error in RDS [ADO]
ms.assetid: cb5a68f8-dba4-41da-bafd-04efe53706b7
author: rothja
ms.author: jroth
ms.openlocfilehash: a0da62851a5cab542a64e219aecc70a13720570f
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759632"
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS &quot; はストリームの読み取り不可エラーを返します &quot;
"ストリームオブジェクトが空であるか、または現在の位置がストリームの末尾にあるため、読み取ることができませんでした。 空でないストリームの場合は、Position プロパティを使用して現在の位置を設定します。 ストリームが空かどうかを確認するには、Size プロパティを確認します。  
  
 このエラーメッセージが表示された場合は、http を介してパラメーター化された階層クエリを使用しようとした可能性があります。 RDS では、パラメーター化された階層をリモートで使用することはできません。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および [Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416) 」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [RDS の基礎](./rds-fundamentals.md)