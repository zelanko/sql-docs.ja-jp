---
title: srv_rpcdb (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_rpcdb
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcdb
ms.assetid: d52bfd22-7a7c-4ab0-af65-df96ff359e6f
author: rothja
ms.author: jroth
ms.openlocfilehash: 38c989a2108a8a877159e9dd5b5c6cffd52ce885
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755905"
---
# <a name="srv_rpcdb-extended-stored-procedure-api"></a>srv_rpcdb (拡張ストアド プロシージャ API)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 現在のリモート ストアド プロシージャのデータベース名部分を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DBCHAR * srv_rpcdb (  
SRV_PROC * srvproc,int *len );  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。 この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。  
  
 *len*  
 データベース名の長さを受け取る **int** 型変数を指すポインターです。 *len* が NULL の場合、データベース名の長さは返されていません。  
  
## <a name="returns"></a>戻り値  
 現在のリモート ストアド プロシージャの名前部分を表した NULL 終端文字列を指す DBCHAR ポインターです。 現在のリモート ストアド プロシージャがない場合は、NULL が返され、*len* パラメーターが - 1 に設定されます。  
  
## <a name="remarks"></a>Remarks  
 この関数は、リモート ストアド プロシージャ オブジェクト名のデータベース部分だけを返します。 所有者、リモート ストアド プロシージャ名、およびリモート ストアド プロシージャ番号に対応する省略可能な各指定子は含まれません。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。  
  
  
