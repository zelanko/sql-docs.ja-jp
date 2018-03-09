---
title: "Windows アプリケーション ログの表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application logs [SQL Server]
- Windows application logs [SQL Server]
- viewing Windows application logs
- errors [SQL Server], logs
- system logs [SQL Server]
- security logs [SQL Server]
- displaying Windows application logs
- logs [SQL Server], Windows application logs
ms.assetid: f9853b74-7db7-47cc-b957-e49ed5bc0a1a
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aa51f2ac0faf762c02adfefc20691e8dbd784454
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="viewing-the-windows-application-log"></a>Windows アプリケーション ログの表示
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が Microsoft Windows アプリケーション ログを使用するように構成されている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各セッションでは新しいイベントが書き込まれます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログとは異なり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを開始するたびに新しいアプリケーション ログが作成されることはありません。  
  
 Windows イベント ビューアーまたは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のログ ビューアーを使用して、Windows アプリケーション ログを表示および管理します。  
  
 イベント ビューアーでは、次の 3 つのログを表示できます。  
  
|Windows ログの種類|Description|  
|----------------------|-----------------|  
|システム ログ|Windows オペレーティング システムのコンポーネントによってログに記録されるイベントを記録します。 たとえば、起動時にドライバーや他のシステム コンポーネントの読み込みが失敗した場合には、システム ログに記録されます。|  
|Security log|失敗したログイン試行などのセキュリティ イベントを記録します。 これは、セキュリティ システムへの変更を監視し、セキュリティ侵害のおそれのある箇所を特定するために役立ちます。 たとえば、システムへのログオン試行は、User Manager の監査設定によってセキュリティ ログに記録できます。<br /><br /> **sysadmin** 固定サーバー ロールのメンバーだけが、セキュリティ ログを表示できます。|  
|アプリケーション ログ|アプリケーションによってログに記録されるイベントを記録します。 たとえば、データベース アプリケーションは、アプリケーション ログにファイル エラーを記録することがあります。|  
  
 イベント ビューアーの使用方法、アプリケーション ログの管理方法、および表示される情報の解釈方法の詳細については、Windows のマニュアルを参照してください。  
  
 **Windows アプリケーション ログを表示するには**  
  
 [Windows アプリケーション ログの表示 &#40;Windows&#41;](../../relational-databases/performance/view-the-windows-application-log-windows-10.md)  
  
  
