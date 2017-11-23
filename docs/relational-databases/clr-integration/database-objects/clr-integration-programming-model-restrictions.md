---
title: "CLR 統合プログラミング モデルの制限事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 180f770c24721ef9e8ed84e4d6f01204b0fd42b7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="clr-integration-programming-model-restrictions"></a>CLR 統合プログラミング モデルの制限事項
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]マネージ ストアド プロシージャやその他のマネージ データベース オブジェクトを作成するときはコードのチェックが実行される特定の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]考慮する必要があります。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]まず、データベースに登録されているときに、マネージ コード アセンブリに対する検査は実行を使用して、 **CREATE ASSEMBLY**ステートメントでは、および実行時にもします。 マネージ コードが実行時にもチェックされるのは、実行時に決して到達しないコード パスがアセンブリに含まれる場合があるためです。  このチェックにより、サード パーティ アセンブリを柔軟に登録できます。特に、クライアント環境での実行を目的に作成され、ホストされた CLR では実行されない "安全でない" コードを含むアセンブリをブロックしないようにすることができるため、サード パーティ アセンブリに柔軟に対応できます。 マネージ コードが満たす必要がある要件として、アセンブリが登録されているかどうかによって変わります**セーフ**、 **EXTERNAL_ACCESS**、または**UNSAFE**、**セーフ** 、最も制限の厳しい、され、次のとおりです。  
  
 マネージ コード アセンブリには、制限事項に加えてコード セキュリティ権限も付与されます。 共通言語ランタイム (CLR) では、マネージ コードに対してコード アクセス セキュリティ (CAS) というセキュリティ モデルがサポートされます。 このモデルでは、コードの ID に基づいてアセンブリに権限が許可されます。 **安全な**、 **EXTERNAL_ACCESS**、および**UNSAFE**アセンブリが別の CAS 権限を持っています。 詳細については、次を参照してください。 [CLR 統合のコード アクセス セキュリティ](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)です。  
  
## <a name="create-assembly-checks"></a>CREATE ASSEMBLY チェック  
 ときに、 **CREATE ASSEMBLY**ステートメントを実行する、セキュリティ レベルごとに、次のチェックが実行されます。  いずれかのチェックが失敗した場合**CREATE ASSEMBLY**はエラー メッセージで失敗します。  
  
### <a name="global-any-security-level"></a>グローバル (すべてのセキュリティ レベル)  
 参照されるすべてのアセンブリは、次の条件のうち 1 つ以上を満たす必要があります。  
  
-   既にデータベースに登録されていること。  
  
-   サポートされているアセンブリの 1 つであること。 詳細については、次を参照してください。[サポートされている .NET Framework ライブラリ](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)です。  
  
-   使用している**アセンブリから作成***\<場所 >、*すべての参照先アセンブリとその依存関係がで利用できる*\<場所 >*.  
  
-   使用している**アセンブリから作成***\<バイト... >、*参照が領域を使用して指定されたすべての区切りのバイトとします。  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 すべて**EXTERNAL_ACCESS**アセンブリは、次の条件を満たす必要があります。  
  
-   静的フィールドが情報の格納に使用されていないこと。 読み取り専用の静的フィールドは許可されます。  
  
-   PEVerify テストにパスしていること。 .NET Framework SDK には、MSIL コードと関連メタデータがタイプ セーフの要件を満たしていることをチェックするための PEVerify ツール (peverify.exe) が付属しています。  
  
-   使用例については、同期、**短期間**クラスは使用されません。  
  
-   ファイナライザー メソッドが使用されていないこと。  
  
 次のカスタム属性で使用できない**EXTERNAL_ACCESS**アセンブリ。  
  
-   System.ContextStaticAttribute  
  
-   System.MTAThreadAttribute  
  
-   System.Runtime.CompilerServices.MethodImplAttribute  
  
-   System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
  
-   System.Runtime.Remoting.Contexts.ContextAttribute  
  
-   System.Runtime.Remoting.Contexts.SynchronizationAttribute  
  
-   System.Runtime.InteropServices.DllImportAttribute  
  
-   System.Security.Permissions.CodeAccessSecurityAttribute  
  
-   System.Security.SuppressUnmanagedCodeSecurityAttribute  
  
-   System.Security.UnverifiableCodeAttribute  
  
-   System.STAThreadAttribute  
  
-   System.ThreadStaticAttribute  
  
### <a name="safe"></a>SAFE  
  
-   すべて**EXTERNAL_ACCESS**アセンブリ条件がチェックされます。  
  
## <a name="runtime-checks"></a>ランタイム チェック  
 コード アセンブリは、実行時に次の条件をチェックされます。 これらの条件のいずれかが見つからなかった場合、マネージ コードの実行が失敗し、例外がスローされます。  
  
### <a name="unsafe"></a>UNSAFE  
 アセンブリの読み込み-呼び出すことによって明示的にするか、 **System.Reflection.Assembly.Load()**メソッドをバイト配列からまたはを使用して暗黙的に**Reflection.Emit**名前空間: は許可されていません。  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 すべて**UNSAFE**条件がチェックされます。  
  
 サポートされているアセンブリの一覧の中で、次のホスト保護属性 (HPA) 値で注釈を付けられている型およびメンバーはすべて許可されません。  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Synchronization  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   UI  
  
 Hpa およびサポートされているアセンブリの許可されない型およびメンバーの一覧の詳細については、次を参照してください。[ホスト保護属性と CLR 統合プログラミング](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)です。  
  
### <a name="safe"></a>SAFE  
 すべて**EXTERNAL_ACCESS**条件がチェックされます。  
  
## <a name="see-also"></a>参照  
 [サポートされている .NET Framework ライブラリ](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)   
 [CLR 統合のコード アクセス セキュリティ](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [ホスト保護属性と CLR 統合プログラミング](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [アセンブリの作成](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
