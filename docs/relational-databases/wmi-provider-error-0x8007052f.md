---
title: WMI エラー 0x8007052f | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: relational-databases-misc
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
caps.latest.revision: 10
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06f5b8000dcd43b12ed5d25ddc733fb892d385f3
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33700565"
---
# <a name="wmi-provider-error-0x8007052f"></a>WMI プロバイダー エラー 0x8007052f
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|0x8007052f|  
|イベント ソース|WMI プロバイダー エラー|  
|コンポーネント|SQL Server 構成マネージャー|  
|シンボル名|NA|  
|メッセージ テキスト|ログオン失敗: ユーザー アカウントの制限。 考えられる原因として、空のパスワードが許可されていない、ログオン時間制限、またはポリシーによる制限が適用されたことなどが挙げられます。|  
  
## <a name="explanation"></a>説明  
 このエラーは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が Windows Server クラスターまたは Windows Server ドメイン コントローラー上で実行されているときに、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーを使用してビルトイン アカウント (Network Service、Local Service、または Local System) に切り替えると発生する場合があります。 Windows Server クラスターまたは Windows Server ドメイン コントローラー上では、ビルトイン アカウントでサービスを実行しないでください。 サービス アカウントに関する推奨事項については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブックの「Windows サービス アカウントの設定」を参照してください。  
  
## <a name="user-action"></a>ユーザーの操作  
 ドメイン アカウントを使用するように [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を構成します。  
  
  
