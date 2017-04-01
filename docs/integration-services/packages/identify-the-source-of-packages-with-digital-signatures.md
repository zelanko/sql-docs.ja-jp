---
title: "デジタル署名を使用してパッケージのソースを特定する | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パッケージの署名 [Integration Services]"
  - "証明書 [Integration Services]"
  - "パッケージ [Integration Services], セキュリティ"
  - "セキュリティ [Integration Services], 証明書"
  - "ポリシーの署名 [Integration Services]"
ms.assetid: a433fbef-1853-4740-9d5e-8a32bc4ffbb2
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# デジタル署名を使用してパッケージのソースを特定する
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージは、そのソースを識別するために、デジタル証明書を使用して署名できます。 パッケージがデジタル証明書を使用して署名されたら、パッケージを読み込む前に [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] でデジタル署名を確認できます。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で署名を確認するには、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] または **dtexec** ユーティリティ (dtexec.exe) でオプションを設定するか、オプションのレジストリ値を設定します。  
  
## デジタル証明書を使用してパッケージに署名する  
 デジタル証明書を使用してパッケージに署名する前に、証明書を取得または作成する必要があります。 証明書を用意したら、この証明書を使用してパッケージに署名できます。 証明書を取得し、その証明書を使用してパッケージに署名する方法の詳細については、「[デジタル証明書を使用してパッケージに署名する](../../integration-services/packages/sign-a-package-by-using-a-digital-certificate.md)」を参照してください。  
  
## パッケージの署名を確認するオプションを設定する  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] と **dtexec** ユーティリティの両方に、署名付きパッケージのデジタル署名を確認するように [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を構成するオプションがあります。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] と **dtexec** ユーティリティのどちらを使用するかは、すべてのパッケージを確認するか特定のパッケージだけを確認するかによって決まります。  
  
-   デザイン時にすべてのパッケージのデジタル署名を確認してからパッケージを読み込むには、 **で** [パッケージの読み込み時にデジタル署名を確認する] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]チェック ボックスをオンにします。 このオプションは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でのすべてのパッケージに対するグローバルな設定です。
  
-   個別のパッケージのデジタル署名を確認するには、**dtexec** ユーティリティを使用してパッケージを実行するときに **/VerifyS[igned]** オプションを指定します。 詳細については、「 [dtexec Utility](../../integration-services/packages/dtexec-utility.md)」を参照してください。  
  
## パッケージの署名を確認するレジストリ値を設定する  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、オプションのレジストリ値である **BlockedSignatureStates**もサポートされています。このレジストリ値を使用すると、署名付きパッケージと署名がないパッケージの読み込みに関する組織のポリシーを管理できます。 このレジストリ値により、パッケージが署名されていない場合、または無効な署名や信頼できない署名が含まれている場合に、パッケージが読み込まれないようにすることができます。 このレジストリ値を設定する方法の詳細については、「[レジストリ値を設定して署名ポリシーを実装する](../../integration-services/packages/implement-a-signing-policy-by-setting-a-registry-value.md)」を参照してください。  
  
> **注:** オプションの **BlockedSignatureStates** レジストリ値では、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] または **dtexec** コマンド ラインで設定されたデジタル署名オプションよりも制限が厳しい設定を指定できます。 この場合、制限が厳しい方のレジストリ設定が他の設定よりも優先されます。  
  
## 参照  
 [Integration Services &#40;SSIS&#41; パッケージ](../../integration-services/integration-services-ssis-packages.md)   
 [セキュリティの概要 &#40;Integration Services&#41;](../../integration-services/security/security-overview-integration-services.md)  
  
  