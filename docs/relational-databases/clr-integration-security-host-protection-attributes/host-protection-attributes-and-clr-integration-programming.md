---
title: 共通言語ランタイム (CLR) ホスト保護属性
description: CLR は、.NET Framework のマネージ API に、共有状態、同期、外部プロセス Mgmt などの属性を付けるメカニズムを提供します。
ms.custom: seo-lt-2019
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- HostProtectionAttribute [CLR integration]
- common language runtime [SQL Server], host protection attributes
- disallowed types and members [CLR integration]
- common language runtime [SQL Server], disallowed types and members
- HPAs [CLR integration]
ms.assetid: 268078df-63ca-4c03-a8e7-7108bcea9697
author: rothja
ms.author: jroth
ms.openlocfilehash: 2aeaeb5d4eb06d6d632a59300225d01cc4376369
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488058"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>ホスト保護属性と CLR 統合プログラミング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  CLR (共通言語ランタイム) には、.NET Framework の一部であるマネージド API (アプリケーション プログラミング インターフェイス) に、特定の属性で注釈を付けるメカニズムが用意されています。このような属性は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降) など CLR のホストのための属性です。 このような HPA (ホスト保護属性) の例としては、次のものがあります。  
  
-   **SharedState**は、API が共有状態 (静的クラス フィールドなど) を作成または管理する機能を公開するかどうかを示します。  
  
-   **同期**: スレッド間で同期を実行する機能を API が公開するかどうかを示します。  
  
-   **外部プロセスMgmt**は、API がホスト プロセスを制御する方法を公開するかどうかを示します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、これらの属性が与えられると、CAS (コード アクセス セキュリティ) を使用して、ホストされた環境で許可されない HPA の一覧を指定します。 CAS の要件は、3 つの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アクセス許可セット **(SAFE、** **EXTERNAL_ACCESS、****または UNSAFE)** のいずれかで指定されます。 これらの 3 つのセキュリティ レベルの 1 つは、アセンブリがサーバーに登録されるときに **、CREATE ASSEMBLY**ステートメントを使用して指定されます。 **SAFE**または**EXTERNAL_ACCESS**アクセス許可セット内で実行されるコードは、**属性**が適用されている特定の型またはメンバーを避ける必要があります。 詳細については、「[アセンブリの作成](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)」および[「CLR 統合プログラミング モデルの制限](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)」を参照してください。  
  
 **HostProtectionAttribute**は、ホストが許可しない可能性のある特定のコード構成要素 (型またはメソッド) を識別するという意味で、信頼性を向上させる方法ほどセキュリティアクセス許可ではありません。 **HostProtectionAttribute**を使用すると、ホストの安定性を保護するプログラミング モデルが適用されます。  
  
## <a name="host-protection-attributes"></a>ホスト保護属性  
 HPA は、ホスト プログラミング モデルに適合しない型またはメンバーを識別して、次に示す信頼性に対する脅威を表します (リスクの低いものから順に並べています)。  
  
-   他の場合には特に害のない脅威  
  
-   サーバーで実行されるマネージ ユーザー コードの不安定化につながる脅威  
  
-   サーバー プロセス自体の不安定化につながる脅威  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**外部プロセスMgmt、****外部スレッド****、MayLeakOnAbort、****セキュリティインフラストラクチャ**、**自己影響するプロセスMgmnt、****自己影響スレッド**化、**共有状態**、**同期**、または**UI**の値を持つ**列挙**を指定する**ホスト保護属性**を持つ型またはメンバーの使用を許可しません。 これにより、状態の共有を可能にしたり、同期を実行するメンバーをアセンブリから呼び出すことができなくなります。さらに、終了時にリソース リークを発生させたり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスの整合性に影響を与える可能性があるメンバーの呼び出しも禁止されます。  
  
### <a name="disallowed-types-and-members"></a>禁止されている型とメンバー  
 次のトピックでは、**ホストプロテクションリソース**の値が によって許可されていない型[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]とメンバーを特定します。  
  
> [!NOTE]  
>  各トピックに含まれる一覧は、サポートされているアセンブリから作成されたものです。  詳細については、「[サポートされる .NET Framework ライブラリ](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Microsoft.VisualBasic.dll の許可されない型およびメンバー](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 HPA の値が許可されない Microsoft.VisualBasic.dll の型およびメンバーの一覧を示します。  
  
 [mscorlib.dll の許可されない型およびメンバー](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-mscorlib-dll.md)  
 HPA の値が許可されない mscorlib.dll の型およびメンバーの一覧を示します。  
  
 [System.dll の許可されない型およびメンバー](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)  
 HPA の値が許可されない System.dll の型およびメンバーの一覧を示します。  
  
 [System.Data.dll の許可されない型およびメンバー](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-data-dll.md)  
 HPA の値が許可されない System.Data.dll の型およびメンバーの一覧を示します。  
  
 [System.Core.dll の許可されない型およびメンバー](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
 HPA の値が許可されない System.Core.dll の型およびメンバーの一覧を示します。  
  
## <a name="see-also"></a>参照  
 [CLR 統合コード アクセス セキュリティ](../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [CLR 統合プログラミング モデルの制限事項](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [アセンブリの作成](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
