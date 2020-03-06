##### approach

1. abstractdao with generics , get which types extending it by using reflection,
 now we have: key, class.
2. persistenceContext to get entitymanager , transaction operation
now we have: key, class, entitymanager
3.  entityManager.unwrap(Session.class)
now we have: key, class, entitymanager, session. We can work now

##### Contents

abstractdao;
key and class;
wrapper class extends serializable

* to get session:
```
Session getSession() {
		return entityManager.unwrap(Session.class);
	}
```
* to get class:
```
this.persistentClass = (Class<T>) ((ParameterizedType) this.getClass().getGenericSuperclass())
				.getActualTypeArguments()[1];
```
* to get entitiyManager:
```
@PersistenceContext	
	protected EntityManager entityManager;
```
* other convenient methods:
```
entityManager.find(persistentClass, key); = getbykey
entityManager.persist(entity); = save
entityManager.flush(); = update
entityManager.remove(entity); = delete
entityManager.remove(entityManager.contains(entity) ? entity : entityManager.merge(entity)); = deletedetached
public List<T> list() {
		CriteriaQuery<T> cq = entityManager.getCriteriaBuilder().createQuery(persistentClass);
		cq.from(persistentClass);
		return entityManager.createQuery(cq).getResultList();
	}
```
* method remove when all data not present:
```
 void deleteDetached(JiraLink jrl) {
		delete(getByKey(jrl.getId()));
	}
```
###### PersistenceContext
//https://stackoverflow.com/questions/19930152/what-is-persistence-context

A PersistenceContext is essentially a Cache. It also tends to have it's own non-shared database connection.
An EntityManager represents a PersistenceContext (and therefore a Cache)
A persistence context is like a cache which contains a set of persistent entities , So once the transaction is finished, all persistent objects are detached from the EntityManager's persistence context and are no longer managed.
