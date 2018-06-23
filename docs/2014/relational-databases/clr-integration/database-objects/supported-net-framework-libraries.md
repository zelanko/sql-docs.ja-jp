---
title: .NET Framework ライブラリのサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1e24738e82e9e73c5777780377207fdc4471aa47
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179329"
---
# <a name="supported-net-framework-libraries"></a>サポートされている .NET Framework ライブラリ
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にホストされている共通言語ランタイム (CLR) を使用すると、ストアド プロシージャ、トリガー、ユーザー定義関数、ユーザー定義型、およびユーザー定義集計をマネージ コードで作成できます。 .NET Framework クラス ライブラリに用意されている機能を使用すると、文字列操作、高度な算術演算、ファイル アクセス、暗号化などの機能を提供する組み込みのクラスにアクセスできます。 これらのクラスは、任意のマネージ ストアド プロシージャ、ユーザー定義型、トリガー、ユーザー定義関数、またはユーザー定義集計からアクセスできます。  
  
> [!NOTE]  
>  サービスまたはグローバル アセンブリ キャッシュ (GAC) にサポートされていないアセンブリをアップグレードする場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 アセンブリの両方にある場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR 統合します。 GAC で、データベースにも登録されているアセンブリ (サポートされていない .NET Framework アセンブリを含む) を提供またはアップグレードする場合は、`ALTER ASSEMBLY` ステートメントを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベース内でもアセンブリのコピーを提供またはアップグレードしてください。 詳細については、次を参照してください。[サポート技術情報の資料 949080](http://support.microsoft.com/kb/949080)です。  
  
## <a name="supported-libraries"></a>サポートされているライブラリ  
 以降で[!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)]サポートされている .NET Framework ライブラリと対話するための信頼性とセキュリティの規格を満たしているテスト済みのリストを持つ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]それらを直接から、グローバル アセンブリ キャッシュ (GAC) に読み込みます。  
  
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
 サポートされていないライブラリは、マネージ ストアド プロシージャ、トリガー、ユーザー定義関数、ユーザー定義型、およびユーザー定義集計から呼び出すことができます。 サポートされていないライブラリをコードで使用するには、`CREATE ASSEMBLY` ステートメントを使用して、これらのライブラリを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに登録する必要があります。 サポートされていないライブラリをサーバーに登録して実行する場合は、そのライブラリのセキュリティと信頼性を確認およびテストする必要があります。  
  
 たとえば、`System.DirectoryServices` 名前空間はサポートされていません。 System.DirectoryServices.dll アセンブリをコードから呼び出す前に、このアセンブリを `UNSAFE` 権限で登録する必要があります。 `UNSAFE` 名前空間内のクラスは `System.DirectoryServices` または `SAFE` の要件を満たさないため、`EXTERNAL_ACCESS` 権限が必要になります。 詳細については、次を参照してください。 [CLR 統合プログラミング モデルの制限事項](clr-integration-programming-model-restrictions.md)と[CLR 統合のコード アクセス セキュリティ](../security/clr-integration-code-access-security.md)です。  
  
## <a name="see-also"></a>参照  
 [アセンブリを作成します。](../assemblies/creating-an-assembly.md)   
 [CLR 統合のコード アクセス セキュリティ](../security/clr-integration-code-access-security.md)   
 [CLR 統合プログラミング モデルの制限事項](clr-integration-programming-model-restrictions.md)  
  
  