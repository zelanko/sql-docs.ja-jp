---
title: "カスタム アセンブリのアクセス許可のアサート |Microsoft ドキュメント"
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
- secure calls [Reporting Services]
- custom assemblies [Reporting Services], permissions
- permission sets [Reporting Services]
- asserting permissions
- permissions [Reporting Services], custom assemblies
- limited permission sets
- security configuration files [Reporting Services]
ms.assetid: 3afb9631-f15e-405e-990b-ee102828f298
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 12e12b61a6b2a2a6a58bb88dd3c4f47c2a6eab22
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="asserting-permissions-in-custom-assemblies"></a>カスタム アセンブリでの権限のアサート
  既定では、カスタム アセンブリ コードの実行が、限られた**実行**権限セットです。 ただし、場合によっては、(ファイルやレジストリなど) セキュリティ システムで保護されたリソースを安全に呼び出すカスタム アセンブリを実装する必要が生じる場合もあります。 そのためには、次の操作を実行する必要があります。  
  
1.  セキュリティで保護された呼び出しを行うために、コードに必要な正しい権限を識別します。 このメソッドの一部である場合、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]ライブラリ、この情報は、メソッドのドキュメントに含める必要があります。  
  
2.  カスタム アセンブリに必要な権限を与えるために、レポート サーバー ポリシーの構成ファイルを変更します。 セキュリティ ポリシーの構成ファイルの詳細については、次を参照してください。[を使用して Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md)です。  
  
3.  セキュリティで保護された呼び出しを行うメソッドの一部として、必要な権限をアサートします。 これは、レポート サーバーによって呼び出されるカスタム アセンブリ コードがレポート式のホスト アセンブリと実行の一部であるために必要**実行**既定のアクセスを許可します。 **実行**アクセス許可セットにより、コードを実行するには保護されたリソースを使用しないようにします。  
  
4.  使用してカスタム アセンブリをマーク**AllowPartiallyTrustedCallersAttribute**厳密な名前で署名されている場合。 これは、カスタム アセンブリは、レポート式のホスト アセンブリを既定が許可されていないの一部であるレポート式から呼び出されるために必要な**FullTrust**;「部分的に信頼された」呼び出し元であるためです。 詳細については、次を参照してください。[付きカスタム アセンブリ](../../reporting-services/custom-assemblies/using-strong-named-custom-assemblies.md)です。  
  
## <a name="implementing-a-secure-call"></a>セキュリティで保護された呼び出しの実装  
 ポリシーの構成ファイルを変更して、アセンブリに特定の権限を与えます。 たとえば、通貨換算を処理するためにカスタム アセンブリを書き込んだ場合、現在の通貨換算レートをファイルから読み取らなければならない場合があります。 換算レート情報を取得する、追加のセキュリティ アクセス許可を追加する必要は**FileIOPermission**アセンブリの権限セットにします。 ポリシーの構成ファイルで次の追加エントリを作成できます。  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="CurrencyRatesFilePermissionSet"  
   Description="A special permission set that grants read access to my currency rates file.">  
      <IPermission class="FileIOPermission"  
         version="1"  
         Read="C:\CurrencyRates.xml"/>  
      <IPermission class="SecurityPermission"  
         version="1"  
         Flags="Execution, Assertion"/>  
</PermissionSet>  
```  
  
 次のように、アセンブリの権限セットを参照するコード グループを追加します。  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="CurrencyRatesFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\MSSQL\Reporting Services\ReportServer\bin\CurrencyConversion.dll"/>  
</CodeGroup>  
```  
  
 コードに適切な権限を取得するためには、カスタム アセンブリ コード内で権限をアサートする必要があります。 たとえば、XML ファイル C:\CurrencyRates.xml の読み取り専用アクセスを追加する場合、次のコードをメソッドに追加する必要があります。  
  
```  
// C#  
FileIOPermission permission = new FileIOPermission(FileIOPermissionAccess.Read, @"C:\CurrencyRates.xml");  
try  
{  
   permission.Assert();  
   // Load the XML currency rates file  
   XmlDocument doc = new XmlDocument();  
   doc.Load(@"C:\CurrencyRates.xml");  
...  
```  
  
 次のように、アサーションをメソッド属性として追加することもできます。  
  
```  
[FileIOPermissionAttribute(SecurityAction.Assert, Read=@"C:\CurrencyRates.xml")]  
```  
  
 詳細については、『.NET Framework 開発者ガイド』の「.NET Framework セキュリティ」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レポートでカスタム アセンブリの使用](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
