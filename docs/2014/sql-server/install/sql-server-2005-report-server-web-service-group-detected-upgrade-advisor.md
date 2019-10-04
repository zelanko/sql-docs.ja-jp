---
title: SQL Server 2005 レポートサーバー Web サービスグループが検出されました (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: bfeff5eae569b481edfcc1cacc89c26e44edaece
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952372"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>SQL Server 2005 レポート サーバー Web サービス グループが検出された (アップグレード アドバイザー)
  アップグレードアドバイザーによって、@no__t 0 のインスタンスが @no__t 1 のレポートサーバー Web サービスグループに関連付けられていることが検出されました。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のネイティブ モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の場合、@no__t 2 レポートサーバー Web サービスグループは使用されません。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードするときに、このサービス グループは削除され、このグループまたはグループに属するユーザーのカスタムのアクセス制御リスト (ACL) はアップグレード中に保持されません。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードする前に、すべてのカスタムの ACL または [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] レポート サーバー Web サービス グループに属するユーザーをバックアップします。 これを行うには、[!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 以降の**Icacls**コマンドラインツール、または @no__t sp2 より前の Windows オペレーティングシステムの cacls.exe コマンドラインツールを使用できます。 これらのツールの構文の詳細については、Windows の製品マニュアルを参照してください。 セットアップが正常に完了した後、カスタムの ACL またはユーザーを、レポート サーバー インスタンスの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート サーバー Windows グループに適用します。 @No__t 0 のレポートサーバー Windows グループは、SQLServerReportServerUser $ @no__t *-1 サーバー*名 >$ @ no__t*instance_name*> の形式になります。  
  
## <a name="see-also"></a>関連項目  
 [アップグレードに関する&#40;問題の Reporting Services アップグレードアドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
