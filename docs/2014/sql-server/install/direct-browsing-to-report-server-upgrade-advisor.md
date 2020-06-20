---
title: レポートサーバーへの直接参照 (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9a12f39bc399e2c46e61fc290bb20ad2c43e4de9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012553"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a>レポート サーバーの直接参照 (アップグレード アドバイザー)
  アップグレードアドバイザーによって、の現在のインストール [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がレポートサーバーの仮想ディレクトリを直接参照していることが検出されました。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 アップグレードアドバイザーによって、の現在のインストール [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がレポートサーバーの仮想ディレクトリ ( **http:// \<server name> /ReportServer**など) を直接参照していることが検出されました。 このような直接参照は現在のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ではサポートされていません。  
  
> [!NOTE]  
>  この規則は警告であり、アップグレードはブロックされません。  
  
## <a name="corrective-action"></a>修正措置  
 ドキュメントライブラリの SharePoint ユーザーインターフェイスを使用して参照するか、 **http:// \<server name> /SharePoint サイト>/_vti_bin/reportserver**を使用します。  
  
  
