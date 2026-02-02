# Repository Cross-Reference Guide

## Purpose

This document provides a comprehensive cross-reference guide for the eight related ERP repositories that inform the enterprise-saas-erp design and architecture. Use this guide to quickly locate specific implementations, patterns, and features across all reference repositories.

---

## Overview of Referenced Repositories

### 1. UniSaaS-ERP
**Repository**: https://github.com/kasunvimarshana/UniSaaS-ERP

**Technology Stack**:
- Backend: Laravel (PHP)
- Frontend: Vue.js with Vite
- Database: PostgreSQL/MySQL
- Infrastructure: Docker, Kubernetes

**Key Features**:
- Comprehensive multi-tenant SaaS ERP
- 8 well-defined core modules (Tenancy, IAM, CRM, Inventory, Billing, Fleet, Analytics, Settings)
- Full Docker Compose setup with Kubernetes manifests
- Complete CI/CD pipelines with GitHub Actions
- Extensive documentation (ARCHITECTURE.md, API_REFERENCE.md, DEPLOYMENT_GUIDE.md)
- Multi-currency, multi-language, multi-branch support

**Best Practices**:
- Clean modular architecture with clear boundaries
- Service-layer orchestration pattern
- Comprehensive Swagger/OpenAPI documentation
- Production-ready containerization

**Use This For**:
- Overall project structure reference
- Multi-tenancy implementation patterns
- Module organization and boundaries
- DevOps and deployment strategies
- Documentation standards

---

### 2. AutoERP
**Repository**: https://github.com/kasunvimarshana/AutoERP

**Technology Stack**:
- Backend: Node.js/Express (API) and Laravel
- Frontend: Vue.js 3 with TypeScript
- Database: PostgreSQL
- Monorepo structure (backend + frontend)

**Key Features**:
- Full TypeScript adoption on frontend
- Domain-specific focus (Vehicle service center management)
- 73 granular permissions with 4 default roles
- Advanced appointment and bay scheduling
- Job card workflows for service management
- Complete test suite (12 tests, 51 assertions)

**Best Practices**:
- TypeScript integration with Vue 3 Composition API
- Type-safe API client implementation
- Granular RBAC system
- Comprehensive testing approach
- Domain-driven design patterns

**Use This For**:
- TypeScript + Vue 3 patterns
- Granular permission system design
- Testing strategies and examples
- Domain-specific module implementation (Fleet/Service)
- Frontend state management with Pinia

---

### 3. erp-saas-core
**Repository**: https://github.com/kasunvimarshana/erp-saas-core

**Technology Stack**:
- Backend: Laravel (pure, minimal dependencies)
- Database: PostgreSQL/MySQL
- Focus: Clean backend architecture

**Key Features**:
- Dynamic CRUD framework with reusable base classes
- Repository pattern implementation
- DTO (Data Transfer Object) usage
- Multi-dimensional support (tenant, vendor, branch, language, currency, unit)
- Configuration-driven queries
- Global search, filtering, sorting capabilities

**Best Practices**:
- SOLID principles throughout
- Clean Laravel foundation without unnecessary abstractions
- Service-layer transaction safety
- Repository pattern for data access
- Tenant-aware global scopes

**Use This For**:
- CRUD framework implementation
- Repository pattern reference
- Service layer architecture
- Clean code principles
- Multi-dimensional data handling

---

### 4. erp-saas-platform
**Repository**: https://github.com/kasunvimarshana/erp-saas-platform

**Technology Stack**:
- Monorepo: Backend (Laravel) + Frontend (Vue.js/TypeScript)
- Database: PostgreSQL
- Focus: Security and platform architecture

**Key Features**:
- Security-first approach with comprehensive security checklist
- Immutable audit trail implementation
- API versioning (v1, v2)
- Monorepo structure with shared contracts
- Secure coding practices and security headers

**Best Practices**:
- Enterprise-grade security implementation
- Audit logging patterns
- API versioning strategy
- Separation of concerns (backend/frontend)
- Unified CI/CD for monorepo

**Use This For**:
- Security implementation patterns
- Audit trail design
- API versioning approach
- Monorepo setup strategies
- Security best practices

---

### 5. saas-erp-foundation
**Repository**: https://github.com/kasunvimarshana/saas-erp-foundation

**Technology Stack**:
- Backend: Node.js/Express
- Frontend: React/Vue.js
- Database: PostgreSQL
- Focus: Documentation and implementation guides

**Key Features**:
- Detailed module implementation guides
- Feature completion checklists
- Payment module implementation
- Invoice module implementation
- User management module
- Role and permission system

**Best Practices**:
- Module-specific documentation
- Step-by-step implementation guides
- Feature checklists for quality assurance
- Clear module boundaries and responsibilities

**Use This For**:
- Module planning and documentation
- Implementation guides and best practices
- Feature completion tracking
- Module structure templates
- Quality assurance checklists

---

### 6. PolySaaS-ERP
**Repository**: https://github.com/kasunvimarshana/PolySaaS-ERP

**Technology Stack**:
- Backend: Laravel
- Frontend: Vue.js with Inertia.js
- Database: PostgreSQL
- Infrastructure: Docker

**Key Features**:
- Polymorphic multi-tenancy patterns
- Advanced Laravel relationship patterns
- Automated installation scripts
- Environment configuration wizard
- Comprehensive documentation with architecture diagrams

**Best Practices**:
- Polymorphic relationship patterns
- Flexible tenant architecture
- Setup automation
- Installation wizards
- Clear architecture diagrams

**Use This For**:
- Advanced polymorphic patterns
- Tenant isolation strategies
- Automated setup scripts
- Installation automation
- Architecture documentation

---

### 7. OmniSaaS-ERP
**Repository**: https://github.com/kasunvimarshana/OmniSaaS-ERP

**Technology Stack**:
- Backend: Laravel
- Frontend: Vue.js
- Database: PostgreSQL
- Infrastructure: Docker, Kubernetes

**Key Features**:
- Enterprise-grade architecture
- API-first design approach
- Production-ready patterns
- Multiple API versions (v1, v2)
- Comprehensive development checklists

**Best Practices**:
- RESTful API best practices
- High-availability architecture
- Scalability considerations
- Professional README structure
- Development workflow checklists

**Use This For**:
- Enterprise design patterns
- API-first approach
- Scalability architecture
- Production deployment patterns
- Professional documentation structure

---

### 8. NexusERP
**Repository**: https://github.com/kasunvimarshana/NexusERP

**Technology Stack**:
- Backend: Laravel 11
- Frontend: Vue.js 3 + TypeScript
- Database: PostgreSQL
- Infrastructure: Docker, Kubernetes

**Key Features**:
- Consolidation of all previous repository learnings
- Comprehensive requirements document (REQUIREMENTS_CONSOLIDATED.md)
- Detailed repository cross-reference (REPOSITORY_CROSS_REFERENCE.md)
- Complete architecture documentation
- Implementation roadmap
- Production-ready setup

**Best Practices**:
- All patterns and practices from previous 7 repositories
- Consolidated requirements
- Comprehensive documentation index
- CRUD framework guide
- Complete setup and deployment guides

**Use This For**:
- Consolidated best practices
- Complete requirements reference
- Architecture patterns
- Implementation planning
- Documentation standards

---

## Quick Reference Matrix

| Feature/Pattern | UniSaaS | AutoERP | Core | Platform | Foundation | PolySaaS | OmniSaaS | Nexus |
|----------------|---------|---------|------|----------|------------|----------|----------|-------|
| **Multi-Tenancy** | ✅ Full | ✅ Full | ✅ Full | ✅ Full | ✅ Full | ✅ Poly | ✅ Full | ✅ Full |
| **TypeScript Frontend** | ❌ | ✅ Full | ❌ | ✅ Partial | ❌ | ❌ | ✅ Partial | ✅ Full |
| **Docker Setup** | ✅ K8s | ✅ Full | ✅ Basic | ✅ Full | ✅ Basic | ✅ Full | ✅ K8s | ✅ K8s |
| **RBAC/ABAC** | ✅ Full | ✅ 73p | ✅ Full | ✅ Full | ✅ Full | ✅ Full | ✅ Full | ✅ Full |
| **Event-Driven** | ✅ Yes | ✅ 25e | ✅ Basic | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Full |
| **API Docs** | ✅ Swagger | ✅ Swagger | ✅ Swagger | ✅ Swagger | ✅ Swagger | ✅ Swagger | ✅ Swagger | ✅ Swagger |
| **Testing** | ⚠️ Partial | ✅ 12t | ⚠️ Partial | ⚠️ Partial | ⚠️ Partial | ⚠️ Partial | ⚠️ Partial | ✅ Full |
| **CI/CD** | ✅ GA | ✅ GA | ✅ GA | ✅ GA | ⚠️ Partial | ✅ GA | ✅ GA | ✅ GA |
| **Documentation** | ✅ Excellent | ✅ Good | ✅ Good | ✅ Good | ✅ Guides | ✅ Good | ✅ Good | ✅ Best |

Legend: 
- ✅ = Full Implementation
- ⚠️ = Partial/Basic
- ❌ = Not Implemented
- GA = GitHub Actions
- K8s = Kubernetes
- Poly = Polymorphic
- 73p = 73 permissions
- 25e = 25 events
- 12t = 12 tests

---

## Common Patterns Across All Repositories

### 1. Controller → Service → Repository Pattern

All repositories consistently follow this layered architecture:

```php
// Controller (thin, handles HTTP)
class ProductController extends Controller
{
    public function __construct(private ProductService $service) {}
    
    public function index(Request $request)
    {
        $products = $this->service->getAll($request->all());
        return ProductResource::collection($products);
    }
}

// Service (business logic, transactions)
class ProductService
{
    public function __construct(private ProductRepository $repository) {}
    
    public function getAll(array $filters): Collection
    {
        DB::beginTransaction();
        try {
            $products = $this->repository->getAll($filters);
            DB::commit();
            return $products;
        } catch (\Exception $e) {
            DB::rollBack();
            throw $e;
        }
    }
}

// Repository (data access)
class ProductRepository
{
    public function getAll(array $filters): Collection
    {
        return Product::query()
            ->when(isset($filters['search']), 
                fn($q) => $q->where('name', 'like', "%{$filters['search']}%"))
            ->get();
    }
}
```

### 2. Multi-Tenancy Implementation

Consistent tenant isolation across all repositories:

```php
// Global Scope
class TenantScope implements Scope
{
    public function apply(Builder $builder, Model $model)
    {
        if (auth()->check() && auth()->user()->tenant_id) {
            $builder->where($model->getTable() . '.tenant_id', 
                auth()->user()->tenant_id);
        }
    }
}

// Model Trait
trait HasTenant
{
    protected static function booted()
    {
        static::addGlobalScope(new TenantScope());
        
        static::creating(function ($model) {
            if (auth()->check() && !$model->tenant_id) {
                $model->tenant_id = auth()->user()->tenant_id;
            }
        });
    }
}
```

### 3. Event-Driven Architecture

Domain events for loose coupling:

```php
// Event
class OrderCreated
{
    public function __construct(public Order $order) {}
}

// Listener
class SendOrderConfirmationEmail
{
    public function handle(OrderCreated $event)
    {
        Mail::to($event->order->customer->email)
            ->send(new OrderConfirmation($event->order));
    }
}

// Service Layer
public function createOrder(array $data): Order
{
    DB::beginTransaction();
    try {
        $order = $this->repository->create($data);
        event(new OrderCreated($order));
        DB::commit();
        return $order;
    } catch (\Exception $e) {
        DB::rollBack();
        throw $e;
    }
}
```

### 4. API Resource Transformers

Consistent API response format:

```php
class ProductResource extends JsonResource
{
    public function toArray($request)
    {
        return [
            'id' => $this->id,
            'name' => $this->name,
            'price' => [
                'amount' => $this->price,
                'currency' => $this->currency,
                'formatted' => $this->formatted_price,
            ],
            'created_at' => $this->created_at->toISOString(),
            'updated_at' => $this->updated_at->toISOString(),
            'category' => new CategoryResource($this->whenLoaded('category')),
        ];
    }
}
```

### 5. Vue 3 Composition API with TypeScript

Modern frontend patterns from AutoERP and NexusERP:

```typescript
<script setup lang="ts">
import { ref, onMounted, computed } from 'vue'
import { useProductStore } from '@/stores/productStore'
import type { Product } from '@/types/models'

const productStore = useProductStore()
const products = ref<Product[]>([])
const loading = ref(false)

const totalProducts = computed(() => products.value.length)

onMounted(async () => {
  loading.value = true
  try {
    products.value = await productStore.fetchProducts()
  } finally {
    loading.value = false
  }
})
</script>
```

---

## Implementation Recommendations for enterprise-saas-erp

### Phase 1: Foundation (Weeks 1-2)
**Primary References**: UniSaaS-ERP, NexusERP

- [ ] Project structure and organization
- [ ] Docker and Docker Compose setup
- [ ] Multi-tenancy foundation with global scopes
- [ ] Basic authentication (Laravel Sanctum)
- [ ] CI/CD pipeline (GitHub Actions)

### Phase 2: Core Architecture (Weeks 3-4)
**Primary References**: erp-saas-core, erp-saas-platform

- [ ] Service-Repository pattern implementation
- [ ] CRUD framework (base classes)
- [ ] DTO implementation
- [ ] Event-driven architecture
- [ ] Security headers and audit trails

### Phase 3: IAM & Authorization (Week 5)
**Primary References**: AutoERP, UniSaaS-ERP

- [ ] RBAC implementation (Spatie Laravel Permission)
- [ ] Granular permissions (based on AutoERP's 73 permissions)
- [ ] Policy-based authorization
- [ ] Multi-factor authentication (MFA)
- [ ] API token management

### Phase 4: Frontend Setup (Week 6)
**Primary References**: AutoERP, NexusERP

- [ ] Vue 3 + TypeScript + Vite setup
- [ ] Pinia state management
- [ ] Vue Router with authentication guards
- [ ] Type-safe API client
- [ ] UI component library (Tailwind CSS + Headless UI)

### Phase 5: Core Modules (Weeks 7-10)
**Primary References**: Multiple (module-specific)

- [ ] Tenant Management (UniSaaS-ERP, PolySaaS-ERP)
- [ ] CRM Module (UniSaaS-ERP, saas-erp-foundation)
- [ ] Inventory Module (erp-saas-core, UniSaaS-ERP)
- [ ] Pricing Engine (erp-saas-core)
- [ ] Billing & Invoicing (saas-erp-foundation)

### Phase 6: Domain-Specific Modules (Weeks 11-12)
**Primary References**: AutoERP (if applicable)

- [ ] Fleet/Vehicle Management (if needed)
- [ ] POS Module
- [ ] eCommerce Integration (optional)
- [ ] Manufacturing/Warehouse (optional)

### Phase 7: Reporting & Analytics (Week 13)
**Primary References**: UniSaaS-ERP, OmniSaaS-ERP

- [ ] Dashboard system
- [ ] Standard reports
- [ ] Custom report builder
- [ ] Analytics and KPIs
- [ ] Data export functionality

### Phase 8: DevOps & Production (Week 14)
**Primary References**: UniSaaS-ERP, OmniSaaS-ERP

- [ ] Kubernetes deployment
- [ ] Monitoring (Prometheus + Grafana)
- [ ] Logging (ELK Stack)
- [ ] Error tracking (Sentry)
- [ ] Performance optimization

### Phase 9: Testing & Documentation (Week 15-16)
**Primary References**: AutoERP, saas-erp-foundation

- [ ] Unit tests
- [ ] Feature tests
- [ ] Integration tests
- [ ] API documentation (Swagger)
- [ ] User guides
- [ ] Deployment documentation

---

## Key Takeaways

### What Makes Each Repository Unique

1. **UniSaaS-ERP**: Most comprehensive, best documentation, production-ready DevOps
2. **AutoERP**: TypeScript mastery, domain specialization, excellent testing
3. **erp-saas-core**: Clean architecture, reusable CRUD framework
4. **erp-saas-platform**: Security-first, audit trails, API versioning
5. **saas-erp-foundation**: Implementation guides, module documentation
6. **PolySaaS-ERP**: Advanced patterns, automated setup
7. **OmniSaaS-ERP**: Enterprise-grade, API-first design
8. **NexusERP**: Consolidated best practices from all repositories

### enterprise-saas-erp Goals

The enterprise-saas-erp repository should:

1. **Consolidate** the best practices from all 8 repositories
2. **Implement** production-ready, enterprise-grade SaaS ERP
3. **Maintain** clean architecture with SOLID principles
4. **Provide** comprehensive documentation
5. **Support** multi-tenancy, multi-currency, multi-language
6. **Include** TypeScript frontend with Vue 3
7. **Offer** flexible module system
8. **Enable** easy customization and extension

---

## Conclusion

This cross-reference guide provides a roadmap for building enterprise-saas-erp by leveraging the collective knowledge and patterns from 8 well-architected ERP repositories. Each repository contributes unique value, and together they form a comprehensive blueprint for a production-ready, enterprise-grade SaaS ERP platform.

**Next Steps**:
1. Review consolidated requirements (see REQUIREMENTS_CONSOLIDATED.md)
2. Study architecture patterns (see ARCHITECTURE.md)
3. Follow implementation roadmap (see IMPLEMENTATION_ROADMAP.md)
4. Set up development environment (see SETUP_GUIDE.md)

---

**Document Version**: 1.0  
**Last Updated**: 2026-02-02  
**Maintainer**: enterprise-saas-erp Development Team
