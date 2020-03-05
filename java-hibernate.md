abstractdao;

key and class;

wrapper class extends serializable

Session getSession() {
		return entityManager.unwrap(Session.class);
	}

this.persistentClass = (Class<T>) ((ParameterizedType) this.getClass().getGenericSuperclass())
				.getActualTypeArguments()[1];

@PersistenceContext	
	protected EntityManager entityManager;


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

//remove when all data not present:

 void deleteDetached(JiraLink jrl) {
		delete(getByKey(jrl.getId()));
	}


//https://stackoverflow.com/questions/19930152/what-is-persistence-context

A PersistenceContext is essentially a Cache. It also tends to have it's own non-shared database connection.
An EntityManager represents a PersistenceContext (and therefore a Cache)
A persistence context is like a cache which contains a set of persistent entities , So once the transaction is finished, all persistent objects are detached from the EntityManager's persistence context and are no longer managed.
