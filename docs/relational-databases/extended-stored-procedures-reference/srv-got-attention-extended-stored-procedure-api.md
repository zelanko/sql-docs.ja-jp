---
title: srv_got_attention (拡張ストアド プロシージャ API) | Microsoft Docs
description: 現在の接続またはタスクを中止する必要があるかどうかを srv_got_attention 確認し、接続が中止された場合、またはバッチが中止された場合に TRUE を返す方法について説明します。
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_got_attention
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
author: rothja
ms.author: jroth
ms.openlocfilehash: 2b5ba738ddd220d83cffe2c28b5629ee491d293f
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248450"
---
# <a name="srv_got_attention-extended-stored-procedure-api"></a>srv_got_attention (拡張ストアド プロシージャ API)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 現在の接続またはタスクを中断する必要があるかどうかをチェックし、接続が強制終了された場合、またはバッチが中断された場合に TRUE を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL srv_got_attention (SRV_PROC *   
srvproc  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *srvproc*  
 データベース接続を特定するポインターです。  
  
## <a name="return-value"></a>戻り値  
 接続が強制終了されたか、バッチが中断された場合に TRUE を返します。 接続またはバッチがアクティブであれば FALSE を返します。  
  
## <a name="remarks"></a>解説  
 実行時間の長い拡張ストアド プロシージャの場合は、**srv_got_attention** を定期的に呼び出してサーバーのアテンションをチェックすることにより、接続が強制終了されたかバッチが中断されたときに、そのプロシージャが自身を終了できるようにする必要があります。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。  
  
  
