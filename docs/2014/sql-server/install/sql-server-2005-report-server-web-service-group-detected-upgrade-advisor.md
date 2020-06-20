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
ms.openlocfilehash: 70be2b9c4e7abd55daaa752830a73cbe6e222659
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054671"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>SQL Server 2005 レポート サーバー Web サービス グループが検出された (アップグレード アドバイザー)
  アップグレードアドバイザーによっ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] て、インスタンスが [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] レポートサーバー Web サービスグループに関連付けられていることが検出されました。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]はを [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用し [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ません。レポートサーバー Web サービスグループ。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードするときに、このサービス グループは削除され、このグループまたはグループに属するユーザーのカスタムのアクセス制御リスト (ACL) はアップグレード中に保持されません。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードする前に、すべてのカスタムの ACL または [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] レポート サーバー Web サービス グループに属するユーザーをバックアップします。 これを行うには、sp2 以降の**Icacls.exe**コマンドラインツール、 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] または sp2 より前の Windows オペレーティングシステムの Cacls.exe コマンドラインツールを使用でき [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] ます。 これらのツールの構文の詳細については、Windows の製品マニュアルを参照してください。 セットアップが正常に完了した後、カスタムの ACL またはユーザーを、レポート サーバー インスタンスの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート サーバー Windows グループに適用します。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]レポートサーバー Windows グループは、SQLServerReportServerUser $ の形式に \<*computer_name*> $ \<*instance_name*> なります。  
  
## <a name="see-also"></a>参照  
 [アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
