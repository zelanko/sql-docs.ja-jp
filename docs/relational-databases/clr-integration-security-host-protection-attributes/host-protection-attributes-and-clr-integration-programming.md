---
title: ホスト保護属性と CLR 統合プログラミング |Microsoft Docs
ms.custom: ''
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
ms.openlocfilehash: 6e060411864c0f354ee9107216b86a47f738bf43
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028065"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>ホスト保護属性と CLR 統合プログラミング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  CLR (共通言語ランタイム) には、.NET Framework の一部であるマネージド API (アプリケーション プログラミング インターフェイス) に、特定の属性で注釈を付けるメカニズムが用意されています。このような属性は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降) など CLR のホストのための属性です。 このような HPA (ホスト保護属性) の例としては、次のものがあります。  
  
-   **SharedState**、共有状態 (静的なクラス フィールドなど) を作成または管理する機能が API で公開するかどうかを示します。  
  
-   **同期**スレッド間で同期を実行する機能が API で公開するかどうかを示します。  
  
-   **ExternalProcessMgmt**、ホスト プロセスを制御する方法が API で公開するかどうかを示します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、これらの属性が与えられると、CAS (コード アクセス セキュリティ) を使用して、ホストされた環境で許可されない HPA の一覧を指定します。 CAS 要件は、3 つのいずれかで指定された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アクセス許可セット。**安全な**、 **EXTERNAL_ACCESS**、または**UNSAFE**します。 サーバーで、アセンブリが登録されているときにこれらの 3 つのセキュリティ レベルのいずれかが指定されてを使用して、 **CREATE ASSEMBLY**ステートメント。 内でコードが実行されて、**セーフ**または**EXTERNAL_ACCESS**特定の型またはメンバーを持つ、アクセス許可セットは避ける必要があります、 **System.Security.Permissions.HostProtectionAttribute**属性が適用されています。 詳細については、次を参照してください。[アセンブリを作成する](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)と[CLR 統合プログラミング モデルの制限事項](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)します。  
  
 **HostProtectionAttribute**でないセキュリティ アクセス許可を固有のコードを識別することで、信頼性を向上させる方法を構築します、型またはメソッドでは、同じくらいこと、ホストを許可しない可能性があります。 使用、 **HostProtectionAttribute**プログラミング モデルにより、ホストの安定性の保護を適用します。  
  
## <a name="host-protection-attributes"></a>ホスト保護属性  
 HPA は、ホスト プログラミング モデルに適合しない型またはメンバーを識別して、次に示す信頼性に対する脅威を表します (リスクの低いものから順に並べています)。  
  
-   他の場合には特に害のない脅威  
  
-   サーバーで実行されるマネージ ユーザー コードの不安定化につながる脅威  
  
-   サーバー プロセス自体の不安定化につながる脅威  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 型またはメンバーを持つの使用が許可されない、 **HostProtectionAttribute**を指定する、 **System.Security.Permissions.HostProtectionResource**列挙の値を持つ**ExternalProcessMgmt**、 **ExternalThreading**、 **MayLeakOnAbort**、 **SecurityInfrastructure**、 **SelfAffectingProcessMgmnt**、 **SelfAffectingThreading**、 **SharedState**、**同期**、または**UI**. これにより、状態の共有を可能にしたり、同期を実行するメンバーをアセンブリから呼び出すことができなくなります。さらに、終了時にリソース リークを発生させたり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスの整合性に影響を与える可能性があるメンバーの呼び出しも禁止されます。  
  
### <a name="disallowed-types-and-members"></a>許可されない型およびメンバー  
 次のトピックでは、特定の型とメンバーが**HostProtectionResource**によって値が許可されない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
> [!NOTE]  
>  各トピックに含まれる一覧は、サポートされているアセンブリから作成されたものです。  詳細については、次を参照してください。[サポートされている .NET Framework ライブラリ](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)します。  
  
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
 [CLR 統合のコード アクセス セキュリティ](../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [CLR 統合プログラミング モデルの制限事項](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [アセンブリの作成](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
