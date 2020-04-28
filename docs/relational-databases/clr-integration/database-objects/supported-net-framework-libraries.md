---
title: サポートされている .NET Framework ライブラリ |Microsoft Docs
description: CLR を SQL Server でホストすると、サポートされている .NET Framework クラスライブラリと、データベースに登録したサポートされていないライブラリを使用して作成できます。
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
author: rothja
ms.author: jroth
ms.openlocfilehash: 459cd091043d567b4c93555c271213d066f3989e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81487116"
---
# <a name="supported-net-framework-libraries"></a>サポートされている .NET Framework ライブラリ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にホストされている共通言語ランタイム (CLR) を使用すると、ストアド プロシージャ、トリガー、ユーザー定義関数、ユーザー定義型、およびユーザー定義集計をマネージド コードで作成できます。 .NET Framework クラス ライブラリに用意されている機能を使用すると、文字列操作、高度な算術演算、ファイル アクセス、暗号化などの機能を提供する組み込みのクラスにアクセスできます。 これらのクラスは、任意のマネージド ストアド プロシージャ、ユーザー定義型、トリガー、ユーザー定義関数、またはユーザー定義集計からアクセスできます。  
  
> [!NOTE]  
>  グローバル アセンブリ キャッシュ (GAC) で、サポートされていないアセンブリを提供またはアップグレードすると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アプリケーションが動作しなくなる可能性があります。 これは、GAC でライブラリを提供またはアップグレードしても [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内でそれらのアセンブリが更新されないためです。 アセンブリが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースと GAC の両方に存在する場合、アセンブリの 2 つのコピーが完全に一致する必要があります。 一致しない場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR 統合によってアセンブリが使用されたときにエラーが発生します。 サポートされていない .NET Framework アセンブリを含め、データベースにも登録されている GAC 内のアセンブリをサービスまたはアップグレードする場合は、 **ALTER assembly**ステートメントを使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]して、データベース内のアセンブリのコピーをサービスまたはアップグレードする必要があります。 詳細については、[サポート技術情報の記事 949080](https://support.microsoft.com/kb/949080)を参照してください。  
  
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
 サポートされていないライブラリは、マネージド ストアド プロシージャ、トリガー、ユーザー定義関数、ユーザー定義型、およびユーザー定義集計から呼び出すことができます。 サポートされていないライブラリは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]コード内で使用する前に、 **CREATE ASSEMBLY**ステートメントを使用してデータベースに登録する必要があります。 サポートされていないライブラリをサーバーに登録して実行する場合は、そのライブラリのセキュリティと信頼性を確認およびテストする必要があります。  
  
 たとえば、 **system.directoryservices**名前空間はサポートされていません。 System.directoryservices アセンブリは、コードから呼び出す前に、 **UNSAFE**アクセス許可を使用して登録する必要があります。 **System.directoryservices**名前空間のクラスが**SAFE**または**EXTERNAL_ACCESS**の要件を満たしていないため、 **UNSAFE**アクセス許可が必要です。 詳細については、「 [Clr 統合プログラミングモデルの制限事項](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)」と「 [Clr 統合コードアクセスセキュリティ](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [アセンブリの作成](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [CLR 統合のコードアクセスセキュリティ](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [CLR 統合プログラミング モデルの制限事項](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)  
  
  
