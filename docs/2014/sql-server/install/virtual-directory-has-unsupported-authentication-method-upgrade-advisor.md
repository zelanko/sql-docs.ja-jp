---
title: 仮想ディレクトリがサポートされていない認証方法 (アップグレード アドバイザー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 216eca6f-9a66-42e1-aa54-dcf99cec9f7d
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 1504b19f521258e2491626540baf49988d7605c4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075436"
---
# <a name="virtual-directory-has-unsupported-authentication-method-upgrade-advisor"></a>仮想ディレクトリにサポートされていない認証方法がある (アップグレード アドバイザー)
  アップグレード アドバイザーによって、レポート マネージャー仮想ディレクトリまたはレポート サーバー仮想ディレクトリで、サポートされていない認証方法が検出されました。 アップグレードでサポートされていない認証方法には、匿名、ダイジェスト、および .NET Passport があります。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のネイティブ モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 セットアップでは、次のいずれかの認証方法を使用する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールをアップグレードすることはできません。  
  
-   匿名  
  
-   ダイジェスト  
  
-   .NET Passport  
  
 続行するには、インターネット インフォメーション サービス (IIS) の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 仮想ディレクトリに指定されている認証方法を変更するか、インストールを移行します。 インストールの移行の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックを参照してください。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードを続行するには、ReportServer および Reports の各仮想ディレクトリに対する IIS の認証方法を変更します。 IIS の認証方法を変更する方法については、IIS のマニュアルを参照してください。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 仮想ディレクトリに対する認証方法を変更した後、アップグレード アドバイザーを再実行して、アップグレードに関する問題がその他にないことを確認します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のアップグレード問題&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  