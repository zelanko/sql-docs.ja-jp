---
title: 多言語展開とグローバルデプロイ
description: マスターデータサービスは、SQL Server によってサポートされるすべての言語でのコンポーネントとツールの展開をサポートしています。
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: c3d485f8-867c-4aa2-a90d-f38fda192534
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7173db1e255f4a7fe4f08a0e57ee80ece3d6c00f
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606254"
---
# <a name="multi-lingual-and-global-deployments-master-data-services"></a>多言語配置とグローバル配置 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でサポートされているすべての言語によるコンポーネントとツールの配置がサポートされています。 詳細については、「 [SQL Server のローカル言語版](../../sql-server/install/local-language-versions-in-sql-server.md)」を参照してください。  
  
## <a name="how-languages-are-used"></a>言語の使用方法  
 次の表では、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] のコンポーネントとツールの言語サポートについて説明します。  
  
|コンポーネントまたはツール|説明|  
|-----------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] セットアップ|セットアップの言語とは異なる言語で [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションを使用できるようにし、サポートされるようにする場合は、英語版のセットアップ プログラムを選択します。 詳細については、下記の [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] の説明を参照してください。|  
|[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]|セットアップの言語によって、 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] の言語が決まります。 たとえば、セットアップの言語としてドイツ語を選択した場合、そのコンピューターでは [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] をドイツ語で使用できます。|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]|セットアップを英語で実行した場合、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションは、すべてのアプリケーション言語で使用でき、サポートされます。 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] は、これらのどのアプリケーション言語でも表示でき、クライアントの Web ブラウザーの言語設定に基づくロケール固有の入力を受け入れます。 言語設定が、サポートされないアプリケーション言語用に構成されている場合、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] は既定で英語に設定されます。<br /><br /> 英語以外の言語でセットアップを実行した場合、他のすべてのアプリケーション言語のリソースが含まれますが、クライアントでは、選択されたセットアップ言語以外の言語で [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] を使用することはできません。 セットアップの言語とは異なる言語で [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] にアクセスしようとすると、アプリケーションでデータ表示およびデータ入力に関する問題が発生することがあります。|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベース|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベース内の情報は、ロケール固有のものではありません。 そのため、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] は、日付や数値などの情報の表示方法を、クライアントの Web ブラウザーの言語設定によって決められた形式で決定することができます。|  
  
## <a name="see-also"></a>参照  
 [マスター データ サービスのインストール](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
