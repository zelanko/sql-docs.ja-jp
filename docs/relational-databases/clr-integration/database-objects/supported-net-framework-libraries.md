---
title: .NET Framework ライブラリのサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
caps.latest.revision: 25
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26f1259cc971e87d42454c881f73f02d7737b4cc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="supported-net-framework-libraries"></a>サポートされている .NET Framework ライブラリ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にホストされている共通言語ランタイム (CLR) を使用すると、ストアド プロシージャ、トリガー、ユーザー定義関数、ユーザー定義型、およびユーザー定義集計をマネージ コードで作成できます。 .NET Framework クラス ライブラリに用意されている機能を使用すると、文字列操作、高度な算術演算、ファイル アクセス、暗号化などの機能を提供する組み込みのクラスにアクセスできます。 これらのクラスは、任意のマネージ ストアド プロシージャ、ユーザー定義型、トリガー、ユーザー定義関数、またはユーザー定義集計からアクセスできます。  
  
> [!NOTE]  
>  グローバル アセンブリ キャッシュ (GAC) で、サポートされていないアセンブリを提供またはアップグレードすると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アプリケーションが動作しなくなる可能性があります。 これは、GAC でライブラリを提供またはアップグレードしても [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内でそれらのアセンブリが更新されないためです。 アセンブリが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースと GAC の両方に存在する場合、アセンブリの 2 つのコピーが完全に一致する必要があります。 一致しない場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR 統合によってアセンブリが使用されたときにエラーが発生します。 提供またはサポートされていない .NET Framework アセンブリを含む、データベースにも登録されている、GAC 内のアセンブリをアップグレードする場合も、サービスまたはアセンブリ内のコピーをアップグレードすることを確認、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベースでは、 **ALTER ASSEMBLY**ステートメントです。 詳細については、次を参照してください。[サポート技術情報の資料 949080](http://support.microsoft.com/kb/949080)です。  
  
## <a name="supported-libraries"></a>サポートされているライブラリ  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には、サポートされている .NET Framework ライブラリの一覧が用意されています。これらのライブラリは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] との連携に必要な信頼性およびセキュリティの基準を満たしていることがテストで確認されています。 サポートされているライブラリは、サーバーに明示的に登録することなく、コードから使用できます。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、グローバル アセンブリ キャッシュ (GAC) からこれらのライブラリを直接読み込みます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の CLR 統合でサポートされるライブラリおよび名前空間を次に示します。  
  
-   CustomMarshalers  
  
-   Microsoft.VisualBasic  
  
-   Microsoft.VisualC  
  
-   mscorlib  
  
-   システム  
  
-   System.Configuration  
  
-   System.Data  
  
-   System.Data.OracleClient  
  
-   System.Data.SqlXml  
  
-   System.Deployment  
  
-   System.Security  
  
-   System.Transactions  
  
-   System.Web.Services  
  
-   System.Xml  
  
-   System.Core.dll  
  
-   System.Xml.Linq.dll  
  
## <a name="unsupported-libraries"></a>サポートされていないライブラリ  
 サポートされていないライブラリは、マネージ ストアド プロシージャ、トリガー、ユーザー定義関数、ユーザー定義型、およびユーザー定義集計から呼び出すことができます。 サポートされていないライブラリを登録する必要があります最初、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を使用して、データベース、 **CREATE ASSEMBLY**ステートメントでは後、コードで使用できます。 サポートされていないライブラリをサーバーに登録して実行する場合は、そのライブラリのセキュリティと信頼性を確認およびテストする必要があります。  
  
 たとえば、 **System.DirectoryServices**名前空間はサポートされていません。 使用して、System.DirectoryServices.dll アセンブリを登録する必要があります**UNSAFE**コードからを呼び出すアクセス許可。 **UNSAFE**のアクセス許可が必要なため内のクラス、 **System.DirectoryServices**名前空間の要件を満たしていない**セーフ**または**EXTERNAL_ACCESS**です。 詳細については、次を参照してください。 [CLR 統合プログラミング モデルの制限事項](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)と[CLR 統合のコード アクセス セキュリティ](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)です。  
  
## <a name="see-also"></a>参照  
 [アセンブリを作成します。](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [CLR 統合のコード アクセス セキュリティ](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [CLR 統合プログラミング モデルの制限事項](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)  
  
  
