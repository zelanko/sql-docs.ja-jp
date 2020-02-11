---
title: 'SQL Server: General Statistics オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:General Statistics
- General Statistics object
ms.assetid: c738e549-d7e7-4211-9ec3-064ac140af7c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a8b2131e4c3c2070bb03018c48294543b9baef02
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250641"
---
# <a name="sql-server-general-statistics-object"></a>SQL Server: General Statistics オブジェクト
  の**SQLServer: General Statistics**オブジェクトに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、現在の接続数や、のインスタンスを実行しているコンピューターから1秒間に接続または切断しているユーザーの数など、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一般的なサーバー全体の利用状況を監視するためのカウンターが用意されています。 これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスとの間で接続と切断を行うクライアントの数が多い、大規模オンライン トランザクション処理 (OLTP) で作業している場合に便利です。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **General Statistics** カウンターについて説明します。  
  
|SQL Server General Statistics カウンター|[説明]|  
|--------------------------------------------|-----------------|  
|**アクティブな一時テーブル**|使用中の一時テーブル/テーブル変数の数。|  
|**1秒あたりの接続リセット数**|接続プールから開始されたログインの総数。|  
|**イベント通知の遅延破棄**|システム スレッドによって削除されるのを待機しているイベント通知の数。|  
|**HTTP 認証済み要求**|秒単位で開始された認証済み HTTP 要求の数。|  
|**論理接続**|システムへの論理接続の数。<br /><br /> 論理接続の主な目的は、複数のアクティブな結果セット (MARS) の要求を処理することです。 MARS 要求の場合、アプリケーションが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続するたびに、1 つの物理接続に複数の論理接続が対応します。<br /><br /> MARS を使用しない場合、物理接続と論理接続の比率は 1:1 です。 したがって、アプリケーションが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続するたびに、論理接続は 1 つずつ増えます。|  
|**ログイン数/秒**|開始されるログインの秒単位の総数。 これには、プールされた接続は含まれません。|  
|**ログアウト/秒**|開始されるログアウトの秒単位の総数。|  
|**Mars デッドロック**|検出された Mars Deadlock の数。|  
|**非アトミックの yield レート**|1 秒間に非アトミックなトランザクションが発生した回数。|  
|**ブロックされたプロセス**|現在ブロックされているプロセスの数。|  
|**SOAP 空の要求**|秒単位で開始された空の SOAP 要求の数。|  
|**SOAP メソッドの呼び出し**|1 秒間に開始された SOAP メソッドの呼び出し数。|  
|**SOAP セッションの開始要求**|1 秒間に開始された SOAP セッション開始要求の数。|  
|**SOAP セッション終了要求**|1 秒間に開始された SOAP セッション終了要求の数。|  
|**SOAP SQL 要求**|1 秒間に開始された SOAP SQL 要求の数。|  
|**SOAP WSDL 要求**|1 秒間に開始された SOAP Web サービス記述言語の要求の数。|  
|**一時テーブルの作成率**|1 秒間に作成された一時テーブル/テーブル変数の数。|  
|**破棄の一時テーブル**|クリーンアップ システム スレッドによって破棄されるのを待機している一時テーブル/テーブル変数の数。|  
|**トレースイベント通知キュー**|Service Broker によって送信されるのを内部キューで待機しているトレース イベント通知インスタンスの数。|  
|**トランザクション**|参加中のトランザクションの数 (ローカル、DTC、およびバインド済みのすべてのトランザクション)。|  
|**ユーザー接続**|SQL Server に現在接続しているユーザー数。|  
  
## <a name="see-also"></a>参照  
 [リソース使用状況の監視 &#40;システムモニタ&#41;](monitor-resource-usage-system-monitor.md)  
  
  
