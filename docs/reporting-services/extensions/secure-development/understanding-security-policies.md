---
title: "セキュリティ ポリシーの概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- code groups [Reporting Services]
- code access security [Reporting Services], security policies
- Execution permission set
- custom assemblies [Reporting Services], security
- permission sets [Reporting Services]
- expressions [Reporting Services], security
- evidence [Reporting Services]
- FullTrust permission set
- security policies [Reporting Services]
- named permission sets [Reporting Services]
ms.assetid: a9bf043a-139a-4929-9a58-244815323df0
caps.latest.revision: 32
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 4cb028a3034ddd4dbee5ee3d1b10f696bbe995f3
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="understanding-security-policies"></a>セキュリティ ポリシーの概要
  レポート サーバーが実行するすべてのコードは、特定のコード アクセス セキュリティ ポリシーの一部である必要があります。 これらのセキュリティ ポリシーは、証拠と名前付き権限セットとを対応付けるコード グループで構成されます。 多くの場合、コード グループは、そのグループ内のコードに対して与えることのできる権限が指定された名前付き権限セットに関連付けられます。 ランタイムは、信頼されるホストまたはローダーが提供した証拠を使用して、コードが属するコード グループ、およびコードに付与された権限を確認します。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]によって定義された、このセキュリティ ポリシー アーキテクチャに準拠、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]共通言語ランタイム (CLR)。 ここでは、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の各種コードおよび関連付けられたポリシー ルールについて説明します。  
  
## <a name="report-server-assemblies"></a>レポート サーバーのアセンブリ  
 レポート サーバーのアセンブリには、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 製品の一部であるコードが含まれています。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] はマネージ コード アセンブリを使用して記述されています。これらのアセンブリにはすべて厳密な名前が付けられています。つまり、デジタル署名されています。 使用してこれらのアセンブリのコード グループを定義、 **StrongNameMembershipCondition**アセンブリの厳密な名前の公開キー情報に基づいて証拠を提供します。 コード グループに与えられますが、 **FullTrust**権限セットです。  
  
## <a name="report-server-extensions-rendering-data-delivery-and-security"></a>レポート サーバーの拡張機能 (表示、データ、配信、およびセキュリティ)  
 レポート サーバーの拡張機能はカスタムのデータ、配信、表示、およびセキュリティ拡張機能であり、ユーザーまたは他のサード パーティが [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の機能を強化するために作成します。 付与する必要があります**FullTrust**これらにポリシー構成ファイルの拡張機能またはアセンブリのコードに関連付けられている、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]を拡張するコンポーネントです。 一部として出荷される拡張機能[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]はレポート サーバーの公開キーで署名の送受信、 **FullTrust**権限セットです。  
  
> [!IMPORTANT]  
>  変更する必要があります、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]許可するポリシー構成ファイル**FullTrust**サード パーティ製の拡張機能です。 コード グループを追加しない場合**FullTrust**は、カスタムの拡張機能のレポート サーバーで使用できません。  
  
 内のポリシー構成ファイルの詳細については[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]を参照してください[を使用して Reporting Services Security Policy Files](../../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md)です。  
  
## <a name="expressions-used-in-reports"></a>レポートで使用される式  
 レポートの式は、インライン コード式またはユーザー定義のメソッド内に含まれる、**コード**レポート定義言語ファイルの要素。 これらの式を付与するポリシー ファイルで既に構成されているコード グループがある、**実行**アクセス許可が既定で設定します。 コード グループは、次のようになります。  
  
```  
<CodeGroup  
   class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="Execution"  
   Name="Report_Expressions_Default_Permissions"  
   Description="This code group grants default permissions for code in report expressions and Code element. ">  
    <IMembershipCondition  
       class="StrongNameMembershipCondition"  
       version="1"  
       PublicKeyBlob="002400..."  
    />  
</CodeGroup>  
```  
  
 **実行**コードが実行を許可 (execute) が保護されたリソースを使用します。 レポート内のすべての式はアセンブリ ("式のホスト" アセンブリ) にコンパイルされます。アセンブリはコンパイルされたレポートの一部として格納されます。 レポートを実行すると、レポート サーバーが式のホスト アセンブリを読み込み、そのアセンブリに対して、式を実行するための呼び出しを行います。 式のホスト アセンブリは、式のホストすべてのコード グループの定義に使用される特定のキーで署名されます。  
  
 レポートの式はレポート オブジェクト モデル コレクション (フィールド、パラメーターなど) を参照し、算術演算や文字列操作などの単純なタスクを実行します。 これらの単純な操作を実行するコードだけが必要です。**実行**権限です。 既定では、ユーザー定義メソッドで、**コード**要素とすべてのカスタム アセンブリが付与されて**実行**でアクセス許可[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]です。 したがって、現在の構成では、ほとんどの式に対してセキュリティ ポリシー ファイルを修正する必要がありません。 式のホスト アセンブリに追加権限を付与するには、管理者がレポート サーバーとレポート デザイナーのポリシー構成ファイルを修正し、レポート式のコード グループを変更する必要があります。 グローバル設定であるため、式のホストの既定の権限を変更すると、すべてのレポートに影響します。 この理由から、追加セキュリティを必要とするすべてのコードをカスタム アセンブリ内に配置することを強くお勧めします。 必要な権限は、このアセンブリにのみ付与します。  
  
> [!IMPORTANT]  
>  外部のアセンブリや保護されたリソースを呼び出すコードは、レポートで使用するカスタム アセンブリに組み込んでください。 そうすることで、コードが要求および表明する権限をより細かく制御できるようになります。 内のメソッドをセキュリティで保護する呼び出しを行う必要がありますいない、**コード**要素。 そう必要があります付与**FullTrust**レポート式のホストと、CLR にすべてのカスタム コードを完全にアクセス許可を付与します。  
  
> [!CAUTION]  
>  付与しないでください**FullTrust**レポート式のホスト用にコード グループにします。 付与した場合は、すべてのレポート式に、保護されたシステム呼び出しを許すことになります。  
  
## <a name="custom-assemblies-referenced-in-reports"></a>レポートで参照されるカスタム アセンブリ  
 一部のレポート式ではサード パーティのコード アセンブリを呼び出すことができます。[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] では、これをカスタム アセンブリとも呼びます。 レポート サーバーにするには、少なくともこれらのアセンブリが必要ですが**実行**ポリシー構成ファイルのアクセスを許可します。 既定では、ポリシー ファイルに付属する[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]付与**実行**"My Computer"ゾーンからすべてのアセンブリへのアクセスを許可します。 カスタム アセンブリには、必要に応じて追加権限を付与できます。  
  
 レポート式の中で、特定のコード権限を必要とする操作を実行しなければならない場合もあります。 典型的な例としては、セキュリティで保護された CLR ライブラリ メソッド (ファイルやシステム レジストリにアクセスするもの) をレポート式から呼び出す場合が挙げられます。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のドキュメントには、このようなセキュリティで保護された呼び出しに必要なコード権限が記載されています。呼び出しを実行するには、セキュリティで保護された特定の権限を呼び出し元コードに付与する必要があります。 レポートの式からの呼び出しを行う場合、または**コード**要素、式のホスト アセンブリは、適切なアクセス許可を付与する必要があります。 ただし、式のホストに権限を付与すると、あらゆる式とレポートで実行するすべてのコードに特定の権限が付与されます。 このような呼び出しはカスタム アセンブリから行うようにし、そのカスタム アセンブリに特定の権限を付与する方が、安全性は高くなります。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のコード アクセス セキュリティ](../../../reporting-services/extensions/secure-development/code-access-security-in-reporting-services.md)   
 [開発 &#40; をセキュリティで保護します。Reporting Services &#41;](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
  
  
