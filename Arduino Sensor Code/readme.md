Create a string of data.....Following the scheme.


@app.route("/")
def session():
    columns = ['tempf', 'tempr', 'fronts', 'rears', 'gx', 'gy', 'gz', 'ax', 'ay', 'az']
    return render_template('session.html', sessionsdata=sessionsdata, columns=columns)

if __name__ == "__main__":
    app.run()
    
    
