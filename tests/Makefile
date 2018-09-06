.PHONY:
all: test

test:
	( \
		source venv/bin/activate; \
		vagrant up --provision; \
	)

prep:
	virtualenv venv
	( \
		source venv/bin/activate; \
		pip install ansible \
	)
	ansible-galaxy install -r roles/requirements.yml -p ./roles/ --force
	cd roles && ln -s ../../ rhsso

clean:
	vagrant destroy -f || true
	rm -f roles/rhsso
	rm -rf roles/redhat-subscription
	rm -f test.retry
	rm -rf venv
