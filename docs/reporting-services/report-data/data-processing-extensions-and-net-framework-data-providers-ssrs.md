---
title: "データ処理拡張機能と .NET Framework データ プロバイダー (SSRS) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reports [Reporting Services], data
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
- report data [Report Builder], accessing
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
caps.latest.revision: 19
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 74e70cd67affe64f31076f362f36e813f3357f82
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="data-processing-extensions-and-net-framework-data-providers-ssrs"></a>データ処理拡張機能と .NET Framework データ プロバイダー (SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ処理拡張機能は、特定の種類のデータ ソースからのデータ取得や、レポート デザインやレポート処理をサポートする追加機能を提供することを目的として、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と共にインストールされるコンポーネントです。 A[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]データ プロバイダーは、コンポーネントから使用可能な[!INCLUDE[msCoName](../../includes/msconame-md.md)]またはサポートするサード パーティ製ソース<xref:System.Data>インターフェイスを取得して、特定の種類のデータ ソースからデータを変更できるようにします。  
  
## <a name="understanding-a-data-processing-extension"></a>データ処理拡張機能について  
 A[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]データ処理拡張機能のサブセットをサポートする、<xref:System.Data>インターフェイスです。 データ処理拡張機能には、データ ソースへの読み取り専用アクセスのみが必要です。書き込みおよび更新用のインターフェイスは実装されていません。 それぞれのデータ処理拡張機能では、レポート処理をサポートするカスタム機能を設定できます。 たとえば、データ処理拡張機能がサポートしている機能の種類は次のとおりです。  
  
-   資格情報を接続文字列とは別に管理  
  
-   複数値パラメーターのサポート  
  
-   データ ソースで計算されたサーバー集計の取得  
  
-   データ ソースからのデータ プロパティおよびデータ値の取得  
  
## <a name="understanding-a-data-provider"></a>データ プロバイダーについて  
 A [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (ドライバーとも呼ばれる) データ プロバイダーは、一連の標準をサポートしている<xref:System.Data>インターフェイスを読み取り、書き込み、およびデータ ソースのデータを更新します。 データ プロバイダーは、特定の種類のデータ ソースに対して使用できるデータ処理拡張機能がない場合に使用できます。 サード パーティの標準 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーは多数あります。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には拡張可能なデータ プロバイダー アーキテクチャがあるので、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ処理拡張機能によって提供される追加機能を含めたカスタムのデータ処理拡張機能を構築することもできます。 詳細については、「 [Implementing a Data Processing Extension](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)」を参照してください。 サード パーティのデータ処理拡張機能の詳細については、サード パーティのデータ処理拡張機能に付属するドキュメントを参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーまたはカスタム データ処理拡張機能を使用してデータ ソースのデータにアクセスするには、インストールと登録が事前に完了している必要があります。 レポートを作成するためのレポート クライアントと、パブリッシュされたレポートを表示するためのレポート サーバーの両方で、データ処理拡張機能をインストールおよび登録する必要があります。 すべてのデータ プロバイダーがサーバー環境で機能するように設計されているわけではありません。 詳細については、「[標準 .NET Framework データ プロバイダーを登録する (SSRS)](../../reporting-services/report-data/register-a-standard-net-framework-data-provider-ssrs.md)」と「[データ処理拡張機能の配置](../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データ処理拡張機能の概要](../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)   
 [レポート埋め込みデータセットおよび共有データセット &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  

